```
sort!(v; alg::Algorithm=defalg(v), lt=isless, by=identity, rev::Bool=false, order::Ordering=Forward)
```

ベクター `v` をその場でソートします。デフォルトでは安定したアルゴリズムが使用されます。特定のアルゴリズムを使用するには、`alg` キーワードを介して選択できます（利用可能なアルゴリズムについては [Sorting Algorithms](@ref) を参照してください）。`by` キーワードを使用すると、比較の前に各要素に適用される関数を提供できます。`lt` キーワードではカスタムの「小さい」関数を提供できます（`x` と `y` のそれぞれについて、`lt(x,y)` と `lt(y,x)` のうちの一方だけが `true` を返すことに注意してください）。`rev=true` を使用すると、ソート順序が逆になります。`rev=true` は前方の安定性を保持します：等しいと比較される要素は逆転されません。これらのオプションは独立しており、すべての可能な組み合わせで一緒に使用できます：`by` と `lt` の両方が指定されている場合、`lt` 関数は `by` 関数の結果に適用されます。`rev=true` は `by` および `lt` キーワードを介して指定された順序を逆転させます。

# 例

```jldoctest
julia> v = [3, 1, 2]; sort!(v); v
3-element Vector{Int64}:
 1
 2
 3

julia> v = [3, 1, 2]; sort!(v, rev = true); v
3-element Vector{Int64}:
 3
 2
 1

julia> v = [(1, "c"), (3, "a"), (2, "b")]; sort!(v, by = x -> x[1]); v
3-element Vector{Tuple{Int64, String}}:
 (1, "c")
 (2, "b")
 (3, "a")

julia> v = [(1, "c"), (3, "a"), (2, "b")]; sort!(v, by = x -> x[2]); v
3-element Vector{Tuple{Int64, String}}:
 (3, "a")
 (2, "b")
 (1, "c")
```
