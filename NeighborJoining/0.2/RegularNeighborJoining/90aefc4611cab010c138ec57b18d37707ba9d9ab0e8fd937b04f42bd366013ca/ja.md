```
regNJ(d::AbstractMatrix{<:Number})
```

regNJアルゴリズムは、以下の文献に基づく従来のNeighborJoiningアルゴリズムです。

> Saitou, N. & Nei, M. The neighbor-joining method: a new method for reconstructing phylogenetic trees. Molecular Biology and Evolution 4, 406-425 (1987).


このアルゴリズムは加法的距離行列に対して木を推測することが保証されていますが、アルゴリズムの複雑さは`O(n^3)`であるため、>10³の距離行列に対しては遅くなる可能性があります。

args:

  * dはn×nの正方形対称距離行列です。

returns:

  * mergesとheightsフィールドを持つNJClust構造体です。

examples:

```@jldoctest
julia> d = [
           0  5  9  9 8
           5  0 10 10 9
           9 10  0  8 7
           9 10  8  0 3
           8  9  7  3 0
       ];

julia> njclusts = regNJ(d)
NJClust{Int64, Float64}([-2 -1; -3 1; -4 2; -5 3], [3.0 2.0; 4.0 3.0; 2.0 2.0; 0.5 0.5])

julia> nwstring = newickstring(njclusts)
"(5:5.000000e-01,(4:2.000000e+00,(3:4.000000e+00,(2:3.000000e+00,1:2.000000e+00):3.000000e+00):2.000000e+00):5.000000e-01):0.000000e+00;"
```
