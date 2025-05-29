```
outofbag(ensemble::Bagging; kwargs...)
```

This method returns the confusion matrix associated to the out of bag error, wherein the succes in predicting instance *i* is calculated on the basis of all models that have not been trained on *i*. The consensus of the different models is a simple majority rule.

The additional keywords arguments are passed to `predict`.
