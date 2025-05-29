```
convert2image(d, i)
convert2image(d, x)
convert2image(DType, x)
```

データセット `d` から観測値 `i` を画像に変換します。また、数値配列 `x` を変換することもできます。

新しいデータセット、例えば `MyDataset` をサポートするためには、`convert2image(::Type{MyDataset}, x::AbstractArray)` を実装してください。

# 例

```julia-repl
julia> using MLDatasets, ImageInTerminal

julia> d = MNIST()

julia> convert2image(d, 1:2) 
# ターミナルに2つの画像が表示されるはずです

julia> x = d[1].features;

julia> convert2image(MNIST, x) # または convert2image(d, x)
```
