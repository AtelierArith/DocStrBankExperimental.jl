```
(l::HashedLocator)(x,t)
```

パラメータ値 `uv⁺ = argmin_uv (X-curve(uv,t))²` を2つのステップで推定します：

1. 初期推定値 `uv=l.hash(x)` を補間します。`x` がハッシュドメインの外にある場合は `uv⁺~uv` を返します。
2. 推定値を洗練するために制約付きニュートンステップ `uv⁺≈l.refine(x,uv,t)` を適用します。
