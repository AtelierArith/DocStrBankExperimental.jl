```
ss_number(code::Union{SSData,AbstractString,AbstractChar})
```

二次構造番号コードを返します。入力は二次構造の `String` コード、二次構造名（`"310 helix"`、`"alpha helix"`、...、`"coil"`）、または `SSData` オブジェクトである可能性があります。

分類は、ProteinSecondaryStructures.jl ドキュメントで説明されている DSSP 標準クラスに従います。

# 例

```jldoctest
julia> using ProteinSecondaryStructures

julia> ss_number("H")
2

julia> ss_number('B')
7

julia> ss_number("beta bridge")
7

julia> ss = SSData("ARG", "A", 1, "H", 0.0, 0.0)
SSData("ARG", "A", 1, "H", 0.0, 0.0)

julia> ss_number(ss)
2

```
