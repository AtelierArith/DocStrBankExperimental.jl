```
lefschetz_filtration(lc::LefschetzComplex, strfilt::Vector{Vector{String}})
```

Lefschetz部分集合に対するフィルトレーションを計算します。

考慮されるLefschetz複体は`lc`で与えられます。文字列ベクトルのベクトル`strfilt`には、フィルトレーションを構築するために必要な単体が含まれています。リスト`strfilt[k]`には、k番目のステップで追加される単体とその閉包が含まれています。したがって、すべてのkに対して、複体`L_k`は、1からkの間のiに対して`strfilt[i]`にリストされたすべてのセルの閉包によって与えられます。この関数は以下の変数を返します：

  * `lcsub`: 部分複体`L_N`、ここで`N = length(strfilt)`
  * `fvalsub`: 値1,...,Nを持つ部分複体のフィルトレーション

# 例

```jldoctest
julia> labels = ["A","B","C","D","E","F","G"];

julia> simplices = [["A","B","D"],["B","D","E"],["B","C","E"],["C","E","F"],["F","G"]];

julia> sc = create_simplicial_complex(labels,simplices);

julia> strfiltration = [["AB","AD","BD"],["BE","DE"],["BCE"],["CF","EF"],["ABD"],["CEF"],["BDE"]];

julia> lcsub, fvalsub = lefschetz_filtration(sc, strfiltration);

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
