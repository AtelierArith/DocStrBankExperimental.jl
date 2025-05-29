```
sctransform([T=Float64], counts::DataMatrix; verbose=true, kwargs...)
```

DataMatrix `counts` の SCTransform を計算します。結果は、スパース項と低ランク項の合計として Matrix Expression に格納されます。すなわち、大きな密行列は作成されません。

オプションで、スパース変換行列の `eltype` を制御するために `T` を指定できます。`T=Float32` を使用すると、結果にほとんど影響を与えずにメモリ使用量を減らすことができます。なぜなら、下流の分析は依然として Float64 で行われるからです。

`kwargs...` の説明については `SCTransformModel` を参照してください。

# 例

SCTransform (遺伝子発現特徴) を計算します：

```
julia> sctransform(counts)
```

SCTransform (抗体キャプチャ特徴) を計算します：

```
julia> sctransform(counts; var_filter = :feature_type => isequal("Antibody Capture"))
```

メモリ使用量を減らすために eltype Float32 を使用して SCTransform (遺伝子発現特徴) を計算します：

```
julia> sctransform(Float32, counts)
```

また、[`SCTransformModel`](@ref) や [`SCTransform.scparams`](https://github.com/rasmushenningsson/SCTransform.jl) も参照してください。
