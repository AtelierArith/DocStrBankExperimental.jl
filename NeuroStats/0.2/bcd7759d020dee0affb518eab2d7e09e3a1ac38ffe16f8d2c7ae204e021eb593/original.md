```
rfz(r)
```

Calculate Fischer's z transformations of correlation coefficient.

# Arguments

  * `r::Float64`: correlation coefficient

# Returns

  * `z::Float64`: z score

# Notes

Formula: `z = atanh(r)`, gives ∞ for r = 1.0 and -∞ for r = -1.0. This functions returns 18.36840028483855 (atanh(1 - eps())) for r = 1.0 and -18.36840028483855 (atanh(1 - eps())) for r = -1.0.
