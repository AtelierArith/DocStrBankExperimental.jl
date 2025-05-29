```
roc(tar, non; laplace; collapse=true, laplace=false)`
```

Computes the essential statistics for evaluation of the performance of a two-class classifier.  The true class of the scores is encoded in the array in which they appear, i.e., `tar`get or `non`-target scores.

The results are given in a type `Roc`, containing the receiver-operating-characteristics (ROC) data for this test.

Optional arguments:

  * `collapse=true`, indicating whether the resulting araays for the probability of

false positives (alarms) and negatives (misses) should be collapsed, i.e., consecutive points on the ROC that have the same false positive or false negatove rate are removed, retaining only the `corner' points of the ROC.

  * `laplace=false`, indicating whether two additional data points at either end of the score scale

should be added to the target and non-target scores.  This corresponds to the Laplace prior, and has a result of limiting the magnitude of the optimal log-likelihood-ratio associated with the line segments of the convex hull of the ROC.
