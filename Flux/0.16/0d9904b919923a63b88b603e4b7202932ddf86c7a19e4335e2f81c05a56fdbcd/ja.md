```
AdaptiveMeanPool(out::NTuple)
```

適応平均プーリング層。出力が `size(y)[1:N] == out` になるように必要なウィンドウサイズを計算します。

入力として `ndims(x) == N+2` の配列を期待します。すなわち、`N` の特徴次元の後にチャネルとバッチ次元があります。ここで、`N = length(out)` です。

他に [`MaxPool`](@ref)、[`AdaptiveMaxPool`](@ref) も参照してください。

# 例

```jldoctest
julia> xs = rand(Float32, 100, 100, 3, 50);  # 50枚のRGB画像のバッチ

julia> AdaptiveMeanPool((25, 25))(xs) |> size
(25, 25, 3, 50)

julia> MeanPool((4,4))(xs) ≈ AdaptiveMeanPool((25, 25))(xs)
true
```
