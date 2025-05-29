```
show_typst(x)
```

Typst形式で`stdout`に出力します。デフォルトおよびカスタム[`context`](@ref)を使用します。

# 例

```jldoctest
julia> show_typst(1 // 2)
$1 / 2$

julia> show_typst(1:4)
$vec(
  1, 2, 3, 4
)$
```
