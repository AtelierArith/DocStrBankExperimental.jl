```
SQLWhereExpression(sql_expression::String, values::T)
SQLWhereExpression(sql_expression::String[, values::Vector{T}])
```

Constructs an instance of SQLWhereExpression, replacing the `?` placeholders inside `sql_expression` with properly quoted values.

# Examples:

```julia
julia> SQLWhereExpression("slug LIKE ?", "%julia%")

SearchLight.SQLWhereExpression
+================+=============+
|            key |       value |
+================+=============+
|      condition |         AND |
+----------------+-------------+
| sql_expression | slug LIKE ? |
+----------------+-------------+
|         values |   '%julia%' |
+----------------+-------------+

julia> SQLWhereExpression("id BETWEEN ? AND ?", [10, 20])

SearchLight.SQLWhereExpression
+================+====================+
|            key |              value |
+================+====================+
|      condition |                AND |
+----------------+--------------------+
| sql_expression | id BETWEEN ? AND ? |
+----------------+--------------------+
|         values |              10,20 |
+----------------+--------------------+

julia> SQLWhereExpression("question LIKE 'what is the question\?'")

SearchLight.SQLWhereExpression
+================+========================================+
|            key |                                  value |
+================+========================================+
|      condition |                                    AND |
+----------------+----------------------------------------+
| sql_expression | question LIKE 'what is the question?'  |
+----------------+----------------------------------------+
|         values |                                        |
+----------------+----------------------------------------+
```
