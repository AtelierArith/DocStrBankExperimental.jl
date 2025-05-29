```
crossvalidate(pl::Machine,X::DataFrame,Y::Vector,sfunc::String="balanced_accuracy_score",nfolds=10)
```

K分割交差検証を実行し、デフォルトでバランス精度を使用します。分類のための以下の指標をサポートしています：

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

および回帰のための以下の指標：

  * "mean*squared*error"
  * "mean*squared*log_error"
  * "median*absolute*error"
  * "r2_score"
  * "max_error"
  * "explained*variance*score"
