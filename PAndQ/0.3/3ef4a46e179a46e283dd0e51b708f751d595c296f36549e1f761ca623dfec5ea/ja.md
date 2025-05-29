```
valuations(atoms)
valuations(p)
```

与えられた `atoms` または `p` に含まれる原子のすべての可能な [評価](https://en.wikipedia.org/wiki/Valuation_(logic)) のイテレータを返します。

# 例

```jldoctest
julia> collect(valuations(⊤))
0次元配列{Vector{Union{}}, 0}:
[]

julia> @atomize collect(valuations(p))
2要素ベクトル{Vector{Pair{PAndQ.Variable, Bool}}}:
 [PAndQ.Variable(:p) => 1]
 [PAndQ.Variable(:p) => 0]

julia> @atomize collect(valuations(p ∧ q))
2×2 行列{Vector{Pair{PAndQ.Variable, Bool}}}:
 [Variable(:p)=>1, Variable(:q)=>1]  [Variable(:p)=>1, Variable(:q)=>0]
 [Variable(:p)=>0, Variable(:q)=>1]  [Variable(:p)=>0, Variable(:q)=>0]
```
