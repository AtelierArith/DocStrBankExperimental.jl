```
Define(; over; args = [], before = nothing, after = nothing)
Define(args...; over, before = nothing, after = nothing)
```

The `Define` node adds or replaces output columns.

By default, new columns are added at the end of the column list while replaced columns retain their position.  Set `after = true` (`after = <column>`) to add both new and replaced columns at the end (after a specified column). Alternatively, set `before = true` (`before = <column>`) to add both new and replaced columns at the front (before the specified column).

# Examples

*Show patients who are at least 16 years old.*

```jldoctest
julia> person = SQLTable(:person, columns = [:person_id, :birth_datetime]);

julia> q = From(:person) |>
           Define(:age => Fun.now() .- Get.birth_datetime, before = :birth_datetime) |>
           Where(Get.age .>= "16 years");

julia> print(render(q, tables = [person]))
SELECT
  "person_2"."person_id",
  "person_2"."age",
  "person_2"."birth_datetime"
FROM (
  SELECT
    "person_1"."person_id",
    (now() - "person_1"."birth_datetime") AS "age",
    "person_1"."birth_datetime"
  FROM "person" AS "person_1"
) AS "person_2"
WHERE ("person_2"."age" >= '16 years')
```

*Conceal the year of birth of patients born before 1930.*

```jldoctest
julia> person = SQLTable(:person, columns = [:person_id, :year_of_birth]);

julia> q = From(:person) |>
           Define(:year_of_birth => Fun.case(Get.year_of_birth .>= 1930,
                                             Get.year_of_birth,
                                             missing));

julia> print(render(q, tables = [person]))
SELECT
  "person_1"."person_id",
  (CASE WHEN ("person_1"."year_of_birth" >= 1930) THEN "person_1"."year_of_birth" ELSE NULL END) AS "year_of_birth"
FROM "person" AS "person_1"
```
