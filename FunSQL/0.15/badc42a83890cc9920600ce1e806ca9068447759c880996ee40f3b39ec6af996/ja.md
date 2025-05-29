```
Sort(; over = nothing, value, nulls = nothing)
Sort(value; over = nothing, nulls = nothing)
Asc(; over = nothing, nulls = nothing)
Desc(; over = nothing, nulls = nothing)
```

ソート順序インジケーター。

[`Order`](@ref) または [`Partition`](@ref) ノードと一緒に使用します。

# 例

*年齢順に患者をリストします。*

```jldoctest
julia> person = SQLTable(:person, columns = [:person_id, :year_of_birth]);

julia> q = From(:person) |>
           Order(Get.year_of_birth |> Desc(nulls = :first));

julia> print(render(q, tables = [person]))
SELECT
  "person_1"."person_id",
  "person_1"."year_of_birth"
FROM "person" AS "person_1"
ORDER BY "person_1"."year_of_birth" DESC NULLS FIRST
```
