```
MMI.fit(conf_model::SimpleInductiveClassifier, verbosity, X, y)
```

For the [`SimpleInductiveClassifier`](@ref) nonconformity scores are computed as follows:

$S_i^{\text{CAL}} = s(X_i, Y_i) = h(\hat\mu(X_i), Y_i), \ i \in \mathcal{D}_{\text{calibration}}$

A typical choice for the heuristic function is $h(\hat\mu(X_i), Y_i)=1-\hat\mu(X_i)_{Y_i}$ where $\hat\mu(X_i)_{Y_i}$ denotes the softmax output of the true class and $\hat\mu$ denotes the model fitted on training data $\mathcal{D}_{\text{train}}$. The simple approach only takes the softmax probability of the true label into account.
