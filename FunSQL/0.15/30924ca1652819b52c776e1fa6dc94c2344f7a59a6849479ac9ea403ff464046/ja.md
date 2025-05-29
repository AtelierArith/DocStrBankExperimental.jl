```
Where(; over = nothing, condition)
Where(condition; over = nothing)
```

`Where`ノードは、指定された`condition`によって入力行をフィルタリングします。

`Where`は`WHERE`句を持つSQLクエリに変換されます：

```sql
SELECT ...
FROM $over
WHERE $condition
```

# 例

```jldoctest
julia> person = SQLTable(:person, columns = [:person_id, :year_of_birth]);

julia> q = From(:person) |>
           Where(Fun(">", Get.year_of_birth, 2000));

julia> print(render(q, tables = [person]))
SELECT
  "person_1"."person_id",
  "person_1"."year_of_birth"
FROM "person" AS "person_1"
WHERE ("person_1"."year_of_birth" > 2000)
```
