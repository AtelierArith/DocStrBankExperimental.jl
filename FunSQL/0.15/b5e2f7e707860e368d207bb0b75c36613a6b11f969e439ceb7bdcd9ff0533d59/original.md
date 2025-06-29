```
Bind(; over = nothing; args)
Bind(args...; over = nothing)
```

The `Bind` node evaluates a query with parameters.  Specifically, `Bind` provides the values for [`Var`](@ref) parameters contained in the `over` node.

In a scalar context, the `Bind` node is translated to a correlated subquery. When `Bind` is applied to the `joinee` branch of a [`Join`](@ref) node, it is translated to a `JOIN LATERAL` query.

# Examples

*Show patients with at least one visit to a heathcare provider.*

```jldoctest
julia> person = SQLTable(:person, columns = [:person_id]);

julia> visit_occurrence = SQLTable(:visit_occurrence, columns = [:visit_occurrence_id, :person_id]);

julia> q = From(:person) |>
           Where(Fun.exists(From(:visit_occurrence) |>
                            Where(Get.person_id .== Var.PERSON_ID) |>
                            Bind(:PERSON_ID => Get.person_id)));

julia> print(render(q, tables = [person, visit_occurrence]))
SELECT "person_1"."person_id"
FROM "person" AS "person_1"
WHERE (EXISTS (
  SELECT "visit_occurrence_1"."visit_occurrence_id"
  FROM "visit_occurrence" AS "visit_occurrence_1"
  WHERE ("visit_occurrence_1"."person_id" = "person_1"."person_id")
))
```

*Show all patients together with the date of their latest visit to a heathcare provider.*

```jldoctest
julia> person = SQLTable(:person, columns = [:person_id]);

julia> visit_occurrence =
           SQLTable(:visit_occurrence, columns = [:visit_occurrence_id, :person_id, :visit_start_date]);

julia> q = From(:person) |>
           LeftJoin(From(:visit_occurrence) |>
                    Where(Get.person_id .== Var.PERSON_ID) |>
                    Order(Get.visit_start_date |> Desc()) |>
                    Limit(1) |>
                    Bind(:PERSON_ID => Get.person_id) |>
                    As(:visit),
                    on = true) |>
            Select(Get.person_id, Get.visit.visit_start_date);

julia> print(render(q, tables = [person, visit_occurrence]))
SELECT
  "person_1"."person_id",
  "visit_1"."visit_start_date"
FROM "person" AS "person_1"
LEFT JOIN LATERAL (
  SELECT "visit_occurrence_1"."visit_start_date"
  FROM "visit_occurrence" AS "visit_occurrence_1"
  WHERE ("visit_occurrence_1"."person_id" = "person_1"."person_id")
  ORDER BY "visit_occurrence_1"."visit_start_date" DESC
  FETCH FIRST 1 ROW ONLY
) AS "visit_1" ON TRUE
```
