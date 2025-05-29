```
resize!(ws, A; kwargs...)
```

`ws`を行列`A`に適したサイズに変更します。`kwargs`は、[`EigenWs`](@ref)を使用する際に、[`Workspace`](@ref)がサポートすべき機能（左および右の固有ベクトルなど）を伝えるために使用できます。この関数は、主に[`LAPACK functions`](@ref LAPACK)内での自動サイズ変更に使用されます。
