```
predict_proba(mix::MixtureModel, y::AbstractVecOrMat; robust=false)
```

Evaluate the probability for each observations to belong to a category given a `MixtureModel`..

  * `robust = true` will prevent the (log)likelihood to under(overflow)flow to `-∞` (or `∞`).
