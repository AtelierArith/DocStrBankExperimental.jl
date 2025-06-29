```
Append(; over = nothing, args)
Append(args...; over = nothing)
```

`Append` concatenates input datasets.

Only the columns that are present in every input dataset will be included to the output of `Append`.

An `Append` node is translated to a `UNION ALL` query:

```sql
SELECT ...
FROM $over
UNION ALL
SELECT ...
FROM $(args[1])
UNION ALL
...
```

# Examples

*Show the dates of all measuments and observations.*

```jldoctest
julia> measurement = SQLTable(:measurement, columns = [:measurement_id, :person_id, :measurement_date]);

julia> observation = SQLTable(:observation, columns = [:observation_id, :person_id, :observation_date]);

julia> q = From(:measurement) |>
           Define(:date => Get.measurement_date) |>
           Append(From(:observation) |>
                  Define(:date => Get.observation_date));

julia> print(render(q, tables = [measurement, observation]))
SELECT
  "measurement_1"."person_id",
  "measurement_1"."measurement_date" AS "date"
FROM "measurement" AS "measurement_1"
UNION ALL
SELECT
  "observation_1"."person_id",
  "observation_1"."observation_date" AS "date"
FROM "observation" AS "observation_1"
```
