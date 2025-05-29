```
eerch(r::ROC)
```

Computes the Equal Error Rate using the Convex Hull interpretation.  This computes the error rate at which the convex hull of the ROC curve crosses the `y=x` diagonal in the ROC.

This value is less sensitive to trial sampling at low number of trials, and has the interpretation of `the maximum while vary prior of the minimum decision costs'–-a useful quantity in decision cost function analysis of a two class classification system.

Arguments:

  * `r::Roc`: an object of type `Roc`, the result of `roc()`
  * `tar, non`: Vectors of target and non-target scores
  * `pfa, pmiss, ch`: Vectors of the false positive and false negative rate, and an array indicating

the membership of the `(pfa, pmiss)` point on the convex hull.  These points are found by `roc()`.
