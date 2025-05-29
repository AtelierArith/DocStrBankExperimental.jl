```
Join(; over = nothing, joinee, on, left = false, right = false, optional = false)
Join(joinee; over = nothing, on, left = false, right = false, optional = false)
Join(joinee, on; over = nothing, left = false, right = false, optional = false)
```

`Join` correlates two input datasets.

The `Join` node is translated to a query with a `JOIN` clause:

```sql
SELECT ...
FROM $over
JOIN $joinee ON $on
```

You can specify the join type:

  * `INNER JOIN` (the default);
  * `LEFT JOIN` (`left = true` or [`LeftJoin`](@ref));
  * `RIGHT JOIN` (`right = true`);
  * `FULL JOIN` (both `left = true` and `right = true`);
  * `CROSS JOIN` (`on = true`).

When `optional` is set, the `JOIN` clause is omitted if the query does not depend on any columns from the `joinee` branch.

To make a lateral join, apply [`Bind`](@ref) to the `joinee` branch.

Use [`As`](@ref) to disambiguate output columns.

# Examples

*Show patients with their state of residence.*

```jldoctest
julia> person = SQLTable(:person, columns = [:person_id, :location_id]);

julia> location = SQLTable(:location, columns = [:location_id, :state]);

julia> q = From(:person) |>
           Join(:location => From(:location),
                Get.location_id .== Get.location.location_id) |>
           Select(Get.person_id, Get.location.state);

julia> print(render(q, tables = [person, location]))
SELECT
  "person_1"."person_id",
  "location_1"."state"
FROM "person" AS "person_1"
JOIN "location" AS "location_1" ON ("person_1"."location_id" = "location_1"."location_id")
```
