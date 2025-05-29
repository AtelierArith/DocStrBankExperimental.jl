```
Limit(; over = nothing, offset = nothing, limit = nothing)
Limit(limit; over = nothing, offset = nothing)
Limit(offset, limit; over = nothing)
Limit(start:stop; over = nothing)
```

The `Limit` node skips the first `offset` rows and then emits the next `limit` rows.

To make the output deterministic, `Limit` must be applied directly after an [`Order`](@ref) node.

The `Limit` node is translated to a query with a `LIMIT` or a `FETCH` clause:

```sql
SELECT ...
FROM $over
OFFSET $offset ROWS
FETCH NEXT $limit ROWS ONLY
```

# Examples

*Show the oldest patient.*

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
