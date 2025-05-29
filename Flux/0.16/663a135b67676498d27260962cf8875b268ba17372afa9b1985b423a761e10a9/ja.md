```
MaxPool(window::NTuple; pad=0, stride=window)
```

ブロックサイズ `window` のすべてのピクセルを1つのピクセルに置き換える最大プーリング層です。

入力として `ndims(x) == N+2` の配列を期待します。すなわち、`N` の特徴次元の後にチャネルとバッチ次元が続きます。ここで `N = length(window)` です。

デフォルトでは、ウィンドウサイズは各次元のストライドでもあります。キーワード `pad` は、`Conv` 層と同じオプションを受け入れます。これには `SamePad()` が含まれます。

他に [`Conv`](@ref)、[`MeanPool`](@ref)、[`AdaptiveMaxPool`](@ref)、[`GlobalMaxPool`](@ref) も参照してください。

# 例

```jldoctest
julia> xs = rand(Float32, 100, 100, 3, 50);  # バッチサイズ50のRGB画像

julia> m = Chain(Conv((5, 5), 3 => 7, pad=SamePad()), MaxPool((5, 5), pad=SamePad()))
Chain(
  Conv((5, 5), 3 => 7, pad=2),          # 532パラメータ
  MaxPool((5, 5), pad=2),
)

julia> m[1](xs) |> size
(100, 100, 7, 50)

julia> m(xs) |> size
(20, 20, 7, 50)

julia> layer = MaxPool((5,), pad=2, stride=(3,))  # 一次元ウィンドウ
MaxPool((5,), pad=2, stride=3)

julia> layer(rand(Float32, 100, 7, 50)) |> size
(34, 7, 50)
```
