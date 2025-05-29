与えられたパウリの集合 S が状態を必ずしも表さない場合、状態を表すパウリの集合 S' を返します。S' は [commutified](@ref commutify) S のスーパーセットです。さらに、S を生成するために必要な削除を表す2つの配列を返します。これは [goodenough2024bipartiteentanglementnoisystabilizer](@cite) に基づいています。

最初の出力配列から S' からキュービットを削除し、次に S' の [`normalizer`](@ref) を取り、その後、S' の [`normalizer`](@ref) から2番目に返された配列のキュービットを削除することで、S が再現されます。

```jldoctest
julia> matroid_parent(T"XX")[1]
+ X_X
+ XX_
+ ZZZ

julia> matroid_parent(T"XX")[2]
3:3

julia> matroid_parent(T"XX")[3]
3:2
```
