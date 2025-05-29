```
BOHB samplers
```

All variable names refer symbols in the [paper](`https://arxiv.org/pdf/1807.01774v1.pdf`)

  * `ρ`: Fraction of random samples
  * `q`: Fraction of best observations to build l and g
  * `N_s`: Sample batch number
  * `N_min`: Minimum number of points to build a model
  * `bw_factor`: Bandwidth factor
  * `D`: Evaluated observations
  * `max_valid_budget`: Maximum budget i that |D_{i}| is big enough to fit a model
  * `N_b`: |D*{max*valid_budget}|
  * `KDE_good`: KDE consists of "good observations", see BOHB paper
  * `KDE_bad`: KDE consists of "bad observations", see BOHB paper
