```
binarize([T::Type,] img, f::AbstractImageBinarizationAlgorithm, args...; kwargs...)
```

アルゴリズム `f` を使用して `img` を二値化します。

# 出力

返される画像 `img₀₁` は `Array{T}` です。

`T` が指定されていない場合、`Gray{eltype(eltype(img))}` として推論されます。これは、`Array{N0f8}` および `Array{Gray{N0f8}}` 型の img に対しては `Gray{N0f8}`、`Array{Float32}` および `Array{Gray{Float32}}` 型の img に対しては `Gray{Float32}` です。

# 例

入力画像とアルゴリズムを `binarize` に渡すだけです。

```julia
img₀₁ = binarize(img, f)
```

これは「`binarize` 画像 `img` を二値化アルゴリズム `f` を使用して」と読み取れます。

返り値の型を明示的に指定することもできます：

```julia
img₀₁_float32 = binarize(Gray{Float32}, img, f)
```

インプレース二値化については [`binarize!`](@ref) を参照してください。
