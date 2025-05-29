eachnondefault(A::DefaultArray, indexstyle = IndexLinear())

`DefaultArray A` の各インデックスを訪問するためのジェネレーターオブジェクトを作成し、非デフォルト値を効率的に処理します。

例:

```julia
julia> A = DefaultArray(1,[1 2; 3 4]);

julia> for i in eachnondefault(A) # 線形インデックス
           println(i, " ", A[i])
       end
4 4
2 3
3 2
```

値 "1" がスキップされていることに注意してください。これは、1をデフォルト値として設定したためです。

```julia
julia> A = DefaultArray(1,[1 2; 3 4]);

julia> for i in eachnondefault(A,IndexCartesian()) # カルテジアンインデックス
           println(i, " ", A[i])
       end
CartesianIndex(2, 2) 4
CartesianIndex(2, 1) 3
CartesianIndex(1, 2) 2
```
