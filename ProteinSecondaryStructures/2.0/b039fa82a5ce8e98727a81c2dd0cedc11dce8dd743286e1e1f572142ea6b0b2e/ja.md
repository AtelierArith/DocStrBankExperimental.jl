```
ss_code(code::Union{SSData,String,Integer})
```

1文字の二次構造コードを返します。入力は二次構造の`Integer`コード、二次構造名（`"310 helix"`、`"alpha helix"`、...、`"coil"`）、または`SSData`オブジェクトである可能性があります。

分類は、ProteinSecondaryStructures.jlのドキュメントで説明されているDSSP標準クラスに従います。

# 例

```jldoctest
julia> using ProteinSecondaryStructures

julia> ss_code(2)
"H"

julia> ss_code("beta bridge")
"B"

julia> ss = SSData("ARG", "A", 1, "H", 0.0, 0.0)
SSData("ARG", "A", 1, "H", 0.0, 0.0)

julia> ss_code(ss)
"H"

```
