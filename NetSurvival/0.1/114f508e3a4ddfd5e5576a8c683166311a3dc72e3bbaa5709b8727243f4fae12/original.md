```
ccolon
```

The `ccolon` dataset provides an example of relative survival dataset from france, and should be paired with the `survexp_fr` ratetable in the `RateTables.jl` package. It contains the following columns: 

  * `time`, in days: follow-up time since diagnosis,
  * `status`, boolean: observed death (1) or censored (0),
  * `age`, in days: age at diagnosis,
  * `year`, in days since 0000-00-00: date of diagnosis,
  * `sex`, `:male` or `:female`,
  * `stage`, interger from 0 to 3, correspnding to Cancer TNM (tumor node metastatis) stages at diagnosis, either I, II, III, IIIb or IV.
  * `side`, the primary tumor location, either `:right` or `:left` of the colon.

This dataset has been studied in [Giorgi2003](@cite), [Wolski2020](@cite) and [Laverny2025](@cite). It contains population-based survival data on cases of colorectal cancer from the Registry of Digestive Cancers in Burgundy, France, diagnosed between 1976 and 1990. Patients were censored 1) after 10 years of followup and 2) on the 31 December 1994. The original data collected were slightly modified for privacy purpose and legal reason. Because of this data perturbation, neither dates nor ages correspond strictly to their real original values. This dataset is therefore provided as a pedagogical and methodological example and should not be used for medical research purposes.

References: 

  * [Giorgi2003](@cite) Giorgi, Roch and Abrahamowicz, Michal and Quantin, Catherine and Bolard, Philippe and Esteve, Jacques and Gouvernet, Joanny and Faivre, Jean. A relative survival regression model using B-spline functions to model non-proportional hazards. Statistics in medicine
  * [Wolski2020](@cite) Wolski, Anna and Graff{'e}o, Nathalie and Giorgi, Roch and {the CENSUR working survival group}. A Permutation Test Based on the Restricted Mean Survival Time for Comparison of Net Survival Distributions in Non-Proportional Excess Hazard Settings. Statistical Methods in Medical Research.
  * [Laverny2025](@cite) Laverny, O., Grafféo, N., & Giorgi, R. (2025). Non-parametric estimation of net survival under dependence between death causes. arXiv preprint arXiv:2502.09273.
