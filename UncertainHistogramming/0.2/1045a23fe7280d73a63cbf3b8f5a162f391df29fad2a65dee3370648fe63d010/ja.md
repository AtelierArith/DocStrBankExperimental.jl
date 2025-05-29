```
kernel(::ContinuousHistogram, ::AbstractArray, data) -> MethodError
kernel(::GaussianHistogram, ::AbstractArray, data)
kernel(::UniformHistogram, ::AbstractArray, data)
```

カーネル関数 $\mathcal{K}(x)$ は、[`ContinuousHistogram`](@ref) を計算するために使用され、次のようになります。

$$
\mathcal{H}(x) = \sum_{i = 1}^M \mathcal{K}_i(x),
$$

ここで、$M$ はデータポイントの総数です。簡潔さのために、すべての `data` 依存性を添字 $i$ を通じて表現しています。

!!! note
    デフォルトでは、`<: ContinuousHistogram` に対しては直接実装されるまで `MethodError` が発生します。

