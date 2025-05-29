```
AdaptiveMaxPool(out::NTuple)
```

適応的最大プーリング層。出力が `size(y)[1:N] == out` となるように必要なウィンドウサイズを計算します。

入力として `ndims(x) == N+2` の配列を期待します。すなわち、`N` の特徴次元の後にチャネルとバッチ次元が続きます。ここで、`N = length(out)` です。

他にも [`MaxPool`](@ref)、[`AdaptiveMeanPool`](@ref) を参照してください。

# 例

```jldoctest
julia> xs = rand(Float32, 100, 100, 3, 50);  # 50枚のRGB画像のバッチ

julia> AdaptiveMaxPool((25, 25))(xs) |> size
(25, 25, 3, 50)

julia> MaxPool((4,4))(xs) ≈ AdaptiveMaxPool((25, 25))(xs)
true
```
