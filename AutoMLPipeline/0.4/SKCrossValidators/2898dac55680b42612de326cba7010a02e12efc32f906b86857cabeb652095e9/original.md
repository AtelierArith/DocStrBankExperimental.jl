```
crossvalidate(pl::Machine,X::DataFrame,Y::Vector,sfunc::String="balanced_accuracy_score",nfolds=10)
```

Runs K-fold cross-validation using balanced accuracy as the default. It support the  following metrics for classification:

  * "accuracy_score"
  * "balanced*accuracy*score"
  * "cohen*kappa*score"
  * "jaccard_score"
  * "matthews_corrcoef"
  * "hamming_loss"
  * "zero*one*loss"
  * "f1_score"
  * "precision_score"
  * "recall_score"

and the following metrics for regression:

  * "mean*squared*error"
  * "mean*squared*log_error"
  * "median*absolute*error"
  * "r2_score"
  * "max_error"
  * "explained*variance*score"
