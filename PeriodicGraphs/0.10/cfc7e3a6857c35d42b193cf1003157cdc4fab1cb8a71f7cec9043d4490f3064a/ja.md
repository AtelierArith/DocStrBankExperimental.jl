```
strong_erings([rs::Vector{Vector{Int}},], g::PeriodicGraph{D}, [depth=15,] ringsymms::AbstractSymmetryGroup=NoSymmetryGroup(length(rs))) where D
```

`g`内の強いエッジリングのリストを計算します。長さは `2*depth+3` までです。オプション引数の意味については、[`strong_rings`](@ref) と [`rings`](@ref) を参照してください。

値の四重項を返します：

  * 最初の2つの値はリングのリストとその対称群であり、`rs`が提供されていない限り、[`strong_rings`](@ref) の結果と同じです（下記参照）。
  * 3番目はエッジリングのリストです：周期グラフの各エッジは整数にマッピングされ、各リングはそのエッジのソートされたリストで表されます。
  * 最後は、エッジから整数へのマッピングであり、[`EdgeDict`](@ref) として与えられます。

`rs`が提供されている場合、最初に返される値は、`rs`のインデックス `keep` のリストであり、`rs[keep]` が強いリングのリストになります。
