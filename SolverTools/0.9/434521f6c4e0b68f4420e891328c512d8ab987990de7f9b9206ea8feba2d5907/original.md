```
ared, pred = aredpred(tr, nlp, f, f_trial, Δm, x_trial, step, slope)
ared, pred = aredpred(tr, nls, Fx, f, f_trial, Δm, x_trial, step, slope)
```

Compute the actual and predicted reductions `∆f` and `Δm`, where `ared = Δf = f_trial - f` is the actual reduction is an objective/merit/penalty function, `pred = Δm = m_trial - m` is the reduction predicted by the model `m` of `f`. We assume that `m` is being minimized, and therefore that `Δm < 0`.

If `tr.good_grad` is `true`, then the gradient of `nlp` at `x_trial` is stored in `tr.gt`. For `AbstractNLSModel`, the argument `Fx` stores the residual if the gradient is updated.
