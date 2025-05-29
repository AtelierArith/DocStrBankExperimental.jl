```
MeanPool(window::NTuple; pad=0, stride=window)
```

平均プーリング層で、`window`サイズのブロック内のすべてのピクセルを平均化します。

入力として、`ndims(x) == N+2`の配列を期待します。すなわち、`N`の特徴次元の後にチャネルとバッチ次元が続きます。ここで、`N = length(window)`です。

デフォルトでは、ウィンドウサイズは各次元のストライドでもあります。キーワード`pad`は、`Conv`層と同じオプションを受け入れます。これには`SamePad()`が含まれます。

他に[`Conv`](@ref)、[`MaxPool`](@ref)、[`AdaptiveMeanPool`](@ref)も参照してください。

# 例

```jldoctest
julia> xs = rand(Float32, 100, 100, 3, 50);

julia> m = Chain(Conv((5,5), 3 => 7), MeanPool((5,5), pad=SamePad()))
Chain(
  Conv((5, 5), 3 => 7),                 # 532 parameters
  MeanPool((5, 5), pad=2),
)

julia> m[1](xs) |> size
(96, 96, 7, 50)

julia> m(xs) |> size
(20, 20, 7, 50)
```
