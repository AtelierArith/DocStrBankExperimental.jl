```
assemble_hmatrix([T,], K, rowtree, coltree;
    adm=StrongAdmissibilityStd(),
    comp=PartialACA(),
    threads=true,
    distributed=false,
    global_index=true)
```

階層行列を組み立てるためのメインルーチン。引数 `K` は近似される行列を表し、`rowtree` と `coltree` はそれぞれ行インデックスと列インデックスを分割する木構造であり、`adm` は `rowtree` のノードと `coltree` のノードで呼び出してブロックが圧縮可能かどうかを判断するために使用され、`comp` は許容可能なブロックを圧縮できる関数/ファンクタです。

`K` が `getindex(K,i,j)` をサポートしていることが前提とされ、`comp` は `comp(K,irange::UnitRange,jrange::UnitRange)` のように呼び出すことができ、`K[irange,jrange]` の圧縮版を [`RkMatrix`](@ref) の形式で生成します。

型パラメータ `T` は行列のエントリの型を指定するために使用され、デフォルトでは `K` から `eltype(K)` を使用して推論されます。
