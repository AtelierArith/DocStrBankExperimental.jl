```
Order(; over = nothing, by)
Order(by...; over = nothing)
```

`Order`は、指定されたキーによって入力行を`by`でソートします。

`Order`ノードは、`ORDER BY`句を持つクエリに変換されます：

```sql
SELECT ...
FROM $over
ORDER BY $by...
```

ソート順は[`Asc`](@ref)、[`Desc`](@ref)、または[`Sort`](@ref)で指定します。

# 例

*年齢順に患者をリストします。*

```jldoctest
julia> person = SQLTable(:person, columns = [:person_id, :year_of_birth]);

julia> q = From(:person) |>
           Order(Get.year_of_birth);

julia> print(render(q, tables = [person]))
SELECT
  "person_1"."person_id",
  "person_1"."year_of_birth"
FROM "person" AS "person_1"
ORDER BY "person_1"."year_of_birth"
```
