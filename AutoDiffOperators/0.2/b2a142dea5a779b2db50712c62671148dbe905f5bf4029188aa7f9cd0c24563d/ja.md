```
with_gradient!!(f, δx, x, ad::ADSelector)
```

関数 `f` の点 `x` における勾配 `∇f(x)` を含むタプル (f(x), ∇f(x)) を返します。

`δx` は再利用または上書きされる場合があり、`∇f(x)` として返されます。

デフォルトの実装は [`with_gradient(f, x, ad)`](@ref) にフォールバックし、`ADSelector` のサブタイプは、より効率的な実装を提供するために `with_gradient!!` を特化させることができます。
