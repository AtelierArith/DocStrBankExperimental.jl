```
colrec
```

The `colrec` dataset provides an example of relative survival dataset from slovenia, and should be paired with the `slopop` ratetable in the `RateTables.jl` package. It contains the following columns: 

  * `time`, in days: follow-up time since diagnosis,
  * `status`, boolean: observed death (1) or censored (0),
  * `age`, in days: age at diagnosis,
  * `year`, in days since 0000-00-00: date of diagnosis,
  * `sex`, `:male` or `:female`,
  * `stage`, cancer stage, can be 1,2,3 or 99 (unknown),
  * `site`, cancer site, can be `:rectum` or `:colon`.

The 5971 patients were diagnosed with colon or rectal cancer in 1994-2000. The original source of the dataset is the [`relsurv` R package](https://CRAN.R-project.org/package=relsurv). Data were provided by the Slovene Cancer Registry. The original data collected were slightly modified for privacy purpose and legal reason. Because of this data perturbation, neither dates nor ages correspond strictly to their real original values. This dataset is therefore provided as a pedagogical and methodological example and should not be used for medical research purposes.

References: 

  * [Pavlik2018](@cite) Pohar Perme, Maja  and Pavlic, Klemen (2018). Nonparametric relative survival analysis with the R package relsurv. Journal of Statistical Software
  * [Zadnik2012](@cite) Zadnik V, Primic Žakelj M, Krajc M (2012). Cancer Burden in Slovenia in Comparison with the Burden in Other European Countries. Zdravniški Vestnik
  * [Zadnik2016](@cite) Zadnik V, Žagar T, Primic Žakelj M (2016). Cancer Patients’ Survival: Standard Calculation Methods and Some Considerations Regarding Their Interpretation. Zdravstveno Varstvo
