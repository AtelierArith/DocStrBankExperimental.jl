```
imon2005(setting)
```

Perform the Imon 2005 algorithm for a given regression setting.

# Arguments

  * `setting::RegressionSetting`: A regression setting.

# Description

The algorithm estimates the GDFFITS diagnostic, which is an extension of well-known regression  diagnostic DFFITS. Unlikely, GDFFITS is used for detecting multiple outliers whereas the original one was used for detecting single outliers. 

# Output

  * `["crit"]`: The critical value used
  * `["gdffits"]`: Array of GDFFITS diagnostic calculated for observations
  * `["outliers"]`: Array of indices of outliers.
  * `["betas"]`: Vector of regression coefficients.

# Notes

The implementation uses LTS rather than LMS as suggested in the paper. 

# References

A. H. M. Rahmatullah Imon (2005) Identifying multiple influential observations in linear regression,  Journal of Applied Statistics, 32:9, 929-946, DOI: 10.1080/02664760500163599
