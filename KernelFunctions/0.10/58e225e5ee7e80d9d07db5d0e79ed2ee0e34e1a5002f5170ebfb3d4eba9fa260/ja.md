```
kernel ∘ transform
∘(kernel, transform)
compose(kernel, transform)
```

入力の変換 `transform` を伴う `kernel` を合成します。

プレフィックス形式は、複数の変換のチェーンをサポートします: `∘(kernel, transform1, transform2) = kernel ∘ transform1 ∘ transform2`。

# 定義

入力 $x, x'$ に対して、入力変換 $t$ によってカーネル $k$ から導出された変換されたカーネル $\widetilde{k}$ は次のように定義されます。

$$
\widetilde{k}(x, x'; k, t) = k\big(t(x), t(x')\big).
$$

# 例

```jldoctest
julia> (SqExponentialKernel() ∘ ScaleTransform(0.5))(0, 2) == exp(-0.5)
true

julia> ∘(ExponentialKernel(), ScaleTransform(2), ScaleTransform(0.5))(1, 2) == exp(-1)
true
```

参照: [`TransformedKernel`](@ref)
