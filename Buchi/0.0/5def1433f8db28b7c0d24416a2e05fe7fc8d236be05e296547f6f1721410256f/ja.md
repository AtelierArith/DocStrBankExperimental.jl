project(A::SpotOmegaWord,inds::Union{Int,Vector{Int}}) project(A::SpotAutomaton,inds::Union{Int,Vector{Int}})

タプルに対する文字から文字へのマップによって単語またはオートマトンを投影します。これは `inds` で指定されます。

例えば、もし `A` がアルファベット `NTuples{3,Ta}` を持っている場合、`project(A,[1,3])` はタプル `(:x,:y,:z)` を `(:x,:z)` にマップし、`project(A,2)` は `(:x,:y,:z)` を `:y` にマップします。一方、もし `A` がアルファベット `Ta` または `Tuple{Ta}` を持っている場合、`project(A,[0,1,0,1])` はそれぞれ `:x`、および `(:x,)` を `(Any,:x,Any,:x)` にマップします。
