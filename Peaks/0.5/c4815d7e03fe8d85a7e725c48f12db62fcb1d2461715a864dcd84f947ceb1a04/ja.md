```
simpleminima(x) -> Vector{Int}
```

`x`の局所的な最小値のインデックスを見つけます。各最小値`i`は、両隣の要素よりも小さいか、または高原の最初のインデックスです。

高原は、連続した等しい（`==`）最小値を持ち、その前後にすぐに大きな値で囲まれた最小値として定義されます。

この関数は`argminima(x, w=1; strict=true)`と意味的に同等ですが、機能が簡素化されているため、より高速です。（速度の違いは`length(x)`に比例します。5k要素を超える入力配列の場合、`argmaxima`はおおよそ7倍遅くなります。）

`missing`を含むベクトルは`simpleminima`ではサポートされていません。この場合は`argminima`を使用してください。

参照: [`argminima`](@ref)

# 例

```julia-repl
julia> simpleminima([3,2,3,1,1,3])
2-element Vector{Int64}:
 2
 4

julia> argminima([3,2,3,1,1,3])
2-element Vector{Int64}:
 2
 4

julia> simpleminima([2,3,1,1])
Int64[]

julia> @btime simpleminima(x) setup=(x = repeat([0,1]; outer=100));
  280.362 ns (3 allocations: 1.00 KiB)

julia> @btime argminima(x) setup=(x = repeat([0,1]; outer=100));
  823.634 ns (3 allocations: 1.00 KiB)
```
