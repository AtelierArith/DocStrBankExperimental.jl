```
convert2image(dataset::ImageNet, i)
convert2image(dataset::ImageNet, x)
```

データセット `d` から観測値 `i` を画像に変換します。また、数値配列 `x` を変換することもできます。

# 例

```julia-repl
julia> using ImageNetDataset, ImageInTerminal

julia> d = ImageNet()

julia> convert2image(d, 1:2)
# ターミナルに2つの画像が表示されるはずです

julia> x = d[1].features;

julia> convert2image(MNIST, x) # または convert2image(d, x)
```
