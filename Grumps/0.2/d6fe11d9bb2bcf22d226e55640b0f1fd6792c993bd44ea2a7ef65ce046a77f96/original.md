```
Estimator( s :: Symbol )
```

Creates and returns a GrumpsEstimator type.

This is one method of specifying the estimator used.  However, it is unforgiving in that the exact symbol used internally must be passed, so the *Estimator( s :: String )* method is usually a better choice.

Possible choices include:

*:cler* the full CLER estimator  

*:cheap* a cheaper alternative to CLER that has the same limit distribution

*:mdle* MDLE, i.e CLER without product level moments

*:shareconstraint* mixed logit with share constraints

*:mixedlogit* mixed logit estimator using micro data only

*:gmm*  GMM estimator of the same model (in progress: not recommended)
