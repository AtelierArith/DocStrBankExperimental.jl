```
ss_name(ss::Union{SSData, Integer, String, Char})
```

二次構造名を返します。入力は `SSData` オブジェクト、二次構造の `Integer` コード (1-10)、または二次構造コード (`G, H, ..., C`) である可能性があります。

分類は、ProteinSecondaryStructures.jl ドキュメントで説明されている DSSP 標準クラスに従います。

## 例

```jldoctest
julia> using ProteinSecondaryStructures

julia> ss_name("H")
"アルファヘリックス"

julia> ss_name(1)
"310ヘリックス"

julia> ss = SSData("ARG", "A", 1, "H", 0.0, 0.0)
SSData("ARG", "A", 1, "H", 0.0, 0.0)

julia> ss_name(ss)
"アルファヘリックス"
```
