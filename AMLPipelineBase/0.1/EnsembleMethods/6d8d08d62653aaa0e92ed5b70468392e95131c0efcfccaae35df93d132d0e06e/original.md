```
fit!(se::StackEnsemble, instances::DataFrame, labels::Vector)
```

Training phase of the stack of learners.

  * perform holdout to obtain indices for
  * partition learner and stacker training sets
  * partition training set for learners and stacker
  * train all learners
  * train stacker on learners' outputs
  * build final model from the trained learners
