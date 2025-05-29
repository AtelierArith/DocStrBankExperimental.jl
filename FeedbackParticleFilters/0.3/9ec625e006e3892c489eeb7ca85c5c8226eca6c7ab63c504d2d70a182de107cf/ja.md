```
ScalarDiffusionStateModel(f::Function, g::Function, init)
```

スカラー拡散過程の隠れ状態モデル $dX_t = f(X_t)dt + g(X_t)dW_t$ を返します。
