```
Limit(; over = nothing, offset = nothing, limit = nothing)
Limit(limit; over = nothing, offset = nothing)
Limit(offset, limit; over = nothing)
Limit(start:stop; over = nothing)
```

`Limit`ノードは最初の`offset`行をスキップし、その後次の`limit`行を出力します。

出力を決定的にするために、`Limit`は[`Order`](@ref)ノードの直後に適用する必要があります。

`Limit`ノードは`LIMIT`または`FETCH`句を持つクエリに変換されます：

```sql
SELECT ...
FROM $over
OFFSET $offset ROWS
FETCH NEXT $limit ROWS ONLY
```

# 例

*最も古い患者を表示します。*

```jldoctest
julia> person = SQLTable(:person, columns = [:person_id, :year_of_birth]);

julia> q = From(:person) |>
           Order(Get.year_of_birth) |>
           Limit(1);

julia> print(render(q, tables = [person]))
SELECT
  "person_1"."person_id",
  "person_1"."year_of_birth"
FROM "person" AS "person_1"
ORDER BY "person_1"."year_of_birth"
FETCH FIRST 1 ROW ONLY
```
