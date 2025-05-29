```
ACOV(c, action = 0)
```

!!! warning
    Experimental


Augmented (adjusted) covariance. Add additional correlations to existed R-part of variance covariance matrix. Can be used with `AR` or `CS` types. 

`action` if existed covariance not equal sero:

  * 0 - add
  * 1 - replace
  * 2 - do nothing (use existed value)
  * 3 - warning and add
  * 4 - warning and replace
  * 5 - warning and use existed value
  * other - error
