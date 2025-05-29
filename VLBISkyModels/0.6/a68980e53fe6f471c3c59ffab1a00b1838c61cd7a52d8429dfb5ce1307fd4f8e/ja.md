```julia
struct Renormalize{T} <: VLBISkyModels.ModelModifier{T}
```

モデルのフラックスを新しい値 `scale*flux(model)` に再正規化します。また、構文糖として Base.:* 演算子をオーバーロードしましたが、これを取り除くかもしれません。

# 例

```julia-repl
julia> modify(Gaussian(), Renormalize(2.0)) == 2.0*Gaussian()
true
```
