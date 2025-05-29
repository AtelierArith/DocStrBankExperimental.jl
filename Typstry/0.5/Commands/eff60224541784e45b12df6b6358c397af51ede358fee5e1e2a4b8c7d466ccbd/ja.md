```
@typst_cmd("s")
typst`s`

スペースで区切られた各パラメータを持つ [`TypstCommand`](@ref) を構築します。

これは補間をサポートしていません。代わりにコンストラクタを使用してください。

# 例

```

jldoctest julia> typst`help` typst`help`

julia> typst`compile input.typ output.typ` typst`compile input.typ output.typ` ```
