非可換のパウリの集合 S に対して、S' を計算し、S の [非可換標準形](@ref canonicalize_noncomm) を得ます。S' の反交換パウリの各ペア Aₖ, Bₖ に対して、集合内の各パウリにキュービットを追加します：Aₖ には X を、Bₖ には Z を、他の演算子には I を追加して S'' を生成します。これにより、完全に可換な集合が得られます。S'' と追加されたキュービットのインデックスのリストを返します。

返されるオブジェクトは、[`matroid_parent`](@ref) 関数にも役立つスタビライザーです。

```jldoctest
julia> commutify(T"XX XZ XY")[1]
+ XXX
+ X__
+ XZZ

julia> commutify(T"XX XZ XY")[2]
3:3
```
