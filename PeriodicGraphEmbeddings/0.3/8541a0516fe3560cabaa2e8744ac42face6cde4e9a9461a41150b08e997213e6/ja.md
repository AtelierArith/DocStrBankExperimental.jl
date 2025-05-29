```
SymmetryGroup3D{T} <: PeriodicGraphs.AbstractSymmetryGroup
```

[`PeriodicGraphEmbedding3D`](@ref)で利用可能な対称操作に関する情報を保存します。

`T`は各個別の[`PeriodicSymmetry3D`](@ref)の数値型パラメータであり、`SymmetryGroup3D`を反復することで取得できます。例えば、`symms`が`SymmetryGroup3D{Rational{Int}}`の場合、`first(symms)`は`PeriodicSymmetry3D{Rational{Int64}}`になります。`collect(symms)`は`SymmetryGroup3D`に保存されている対称の完全なリストを提供します。

`PeriodicGraphEmbedding3D`の対称的にユニークな頂点のリストは、`unique(symms)`を呼び出すことで取得できます。任意の頂点`i`とその対応するユニークな頂点とのマッピングは、`symms`自体を頂点で呼び出すことで取得できます。例えば、`symms(i)`のようにします。
