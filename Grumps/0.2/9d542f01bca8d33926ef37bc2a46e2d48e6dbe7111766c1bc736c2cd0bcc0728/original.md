```
Estimator( s :: String )
```

Creates and returns a GrumpsEstimator type.  Grumps is reasonably good at figuring out what it is that you want, so e.g. *Estimator( "maximum likelihood" )* gives you the unpenalized Grumps maximum likelihood estimator.

The estimators currently programmed include:

  * the full CLER estimator
  * a cheaper alternative to CLER that has the same limit distribution
  * MDLE, i.e CLER without product level moments
  * mixed logit with share constraints
  * mixed logit estimator using micro data only
  * GMM estimators of the same model (in progress: not recommended)
