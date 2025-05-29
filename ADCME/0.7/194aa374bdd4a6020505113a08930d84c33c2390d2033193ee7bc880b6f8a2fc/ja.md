```
placeholder(dtype::Type; kwargs...)
```

タイプ `dtype` のプレースホルダーを作成します。

# 例

```julia
a = placeholder(Float64, shape=[20,10])
b = placeholder(Float64, shape=[]) # スカラー 
c = placeholder(Float64, shape=[nothing]) # ベクトル
```
