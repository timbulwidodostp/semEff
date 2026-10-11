# Olah Data Semarang
# WhatsApp : +6285227746673
# IG : @olahdatasemarang_
# Automatic Calculation of Effects for Piecewise Structural Equation Models Use semEff With (In) R Software
install.packages("semEff")
library("semEff")
# Estimate Automatic Calculation of Effects for Piecewise Structural Equation Models Use semEff With (In) R Software
semEff = read.csv("https://raw.githubusercontent.com/timbulwidodostp/semEff/main/semEff/semEff.csv",sep = ";")
shipley.sem <- list(DD = lme4::lmer(DD ~ lat + (1 | site) + (1 | tree), data = semEff),
Date = lme4::lmer(Date ~ DD + (1 | site) + (1 | tree), data = semEff),
Growth = lme4::lmer(Growth ~ Date + (1 | site) + (1 | tree), data = semEff), 
Live = lme4::glmer(Live ~ Growth + (1 | site) + (1 | tree), binomial, data = semEff))
shipley.sem.boot <- bootEff(shipley.sem, R = 30, seed = 13, ran.eff = "site")
semEff <- semEff(shipley.sem.boot)
summary(semEff)
# Automatic Calculation of Effects for Piecewise Structural Equation Models Use semEff With (In) R Software
# Olah Data Semarang
# WhatsApp : +6285227746673
# IG : @olahdatasemarang_
# Finished