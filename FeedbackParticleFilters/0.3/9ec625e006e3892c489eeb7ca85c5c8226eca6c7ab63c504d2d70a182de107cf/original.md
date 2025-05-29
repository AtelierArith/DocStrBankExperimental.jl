```
ScalarDiffusionStateModel(f::Function, g::Function, init)
```

Returns a scalar diffusion process hidden state model $dX_t = f(X_t)dt + g(X_t)dW_t$.
