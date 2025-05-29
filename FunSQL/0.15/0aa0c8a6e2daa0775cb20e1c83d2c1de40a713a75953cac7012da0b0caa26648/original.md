```
Select(; over; args)
Select(args...; over)
```

The `Select` node specifies the output columns.

```sql
SELECT $args...
FROM $over
```

Set the column labels with [`As`](@ref).

# Examples

*List patient IDs and their age.*

```jldoctest
julia> person = SQLTable(:person, columns = [:person_id, :birth_datetime]);

julia> q = From(:person) |>
           Select(Get.person_id,
                  :age => Fun.now() .- Get.birth_datetime);

julia> print(render(q, tables = [person]))
SELECT
  "person_1"."person_id",
  (now() - "person_1"."birth_datetime") AS "age"
FROM "person" AS "person_1"
```
