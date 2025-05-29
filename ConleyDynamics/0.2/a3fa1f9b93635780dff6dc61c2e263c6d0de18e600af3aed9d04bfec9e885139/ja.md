```
lefschetz_filtration(lc::LefschetzComplex, fvalues::Vector{Int})
```

Lefschetz部分集合に対するフィルトレーションを計算します。

考慮されるLefschetz複体は`lc`で与えられます。ベクトル`fvalues`は、`lc`内のすべてのセルに対して0からNの間の整数を割り当てます。すべてのkに対して、複体`L_k`は値が1からkの間のすべてのセルの閉包によって与えられます。この関数は以下の変数を返します：

  * `lcsub`: サブ複体`L_N`
  * `fvalsub`: 値1,...,Nを持つサブ複体のフィルトレーション

# 例

```jldoctest
julia> labels = ["A","B","C","D","E","F","G"];

julia> simplices = [["A","B","D"],["B","D","E"],["B","C","E"],["C","E","F"],["F","G"]];

julia> sc = create_simplicial_complex(labels,simplices);

julia> filtration = [0,0,0,0,0,0,0,1,1,0,1,2,0,4,2,4,0,5,3,7,6];

julia> lcsub, fvalsub = lefschetz_filtration(sc,filtration);

julia> phinf, phint = persistent_homology(lcsub,fvalsub);

julia> phinf
3-element Vector{Vector{Int64}}:
 [1]
 []
 []

julia> phint
3-element Vector{Vector{Tuple{Int64, Int64}}}:
 []
 [(1, 5), (2, 7), (4, 6)]
 []
```
