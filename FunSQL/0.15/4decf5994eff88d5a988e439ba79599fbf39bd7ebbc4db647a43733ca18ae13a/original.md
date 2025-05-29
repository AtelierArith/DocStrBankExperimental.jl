```
Highlight(; over = nothing; color)
Highlight(color; over = nothing)
```

Highlight `over` with the given `color`.

The highlighted node is printed with the selected color when the query containing it is displayed.

Available colors can be found in `Base.text_colors`.

# Examples

```jldoctest
julia> q = From(:person) |>
           Select(Get.person_id |> Highlight(:bold))
let q1 = From(:person),
    q2 = q1 |> Select(Get.person_id)
    q2
end
```
