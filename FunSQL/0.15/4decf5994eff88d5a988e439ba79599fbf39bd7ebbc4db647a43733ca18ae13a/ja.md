```
Highlight(; over = nothing; color)
Highlight(color; over = nothing)
```

指定された `color` で `over` をハイライトします。

ハイライトされたノードは、それを含むクエリが表示されるときに選択された色で印刷されます。

利用可能な色は `Base.text_colors` で見つけることができます。

# 例

```jldoctest
julia> q = From(:person) |>
           Select(Get.person_id |> Highlight(:bold))
let q1 = From(:person),
    q2 = q1 |> Select(Get.person_id)
    q2
end
```
