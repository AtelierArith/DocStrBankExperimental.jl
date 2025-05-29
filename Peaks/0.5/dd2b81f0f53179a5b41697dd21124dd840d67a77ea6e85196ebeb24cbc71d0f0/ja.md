```
simplemaxima(x) -> Vector{Int}
```

`x`の局所的な最大値のインデックスを見つけます。各最大値`i`は、両隣の要素よりも大きいか、または高原の最初のインデックスです。

高原は、前後により小さい値で囲まれた連続した等しい（`==`）最大値を持つ最大値として定義されます。

この関数は`argmaxima(x, w=1; strict=true)`と意味的に同等ですが、機能が簡素化されているため、より高速です。（速度の違いは`length(x)`に比例し、5k要素を超える入力配列では、`argmaxima`はおおよそ7倍遅くなります。）

`simplemaxima`は`missing`を含むベクトルをサポートしていません。この場合は`argmaxima`を使用してください。

関連情報: [`argmaxima`](@ref)

# 例

```julia-repl
julia> simplemaxima([0,2,0,1,1,0])
2-element Vector{Int64}:
 2
 4

julia> argmaxima([0,2,0,1,1,0])
2-element Vector{Int64}:
 2
 4

julia> simplemaxima([2,0,1,1])
Int64[]

julia> @btime simplemaxima(x) setup=(x = repeat([0,1]; outer=100));
  269.865 ns (3 allocations: 1.00 KiB)

julia> @btime argmaxima(x) setup=(x = repeat([0,1]; outer=100));
  748.780 ns (3 allocations: 1.00 KiB)
```
