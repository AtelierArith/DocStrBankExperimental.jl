```
initrbm(x, nhidden)
initrbm(x, nhidden, rbmtype)
```

Creates a RBM with `nhidden` hidden units and initalizes its weights for training on dataset `x`. `rbmtype` can be a subtype of `AbstractRBM`, default is `BernoulliRBM`.
