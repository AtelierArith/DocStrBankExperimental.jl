```
Agg(; over = nothing, name, args = [], filter = nothing)
Agg(name; over = nothing, args = [], filter = nothing)
Agg(name, args...; over = nothing, filter = nothing)
Agg.name(args...; over = nothing, filter = nothing)
```

An application of an aggregate function.

An `Agg` node must be applied to the output of a [`Group`](@ref) or a [`Partition`](@ref) node.  In a `Group` context, it is translated to a regular aggregate function, and in a `Partition` context, it is translated to a window function.

# Examples

*Number of patients per year of birth.*

```jldoctest
julia> person = SQLTable(:person, columns = [:person_id, :year_of_birth]);

julia> q = From(:person) |>
           Group(Get.year_of_birth) |>
           Select(Get.year_of_birth, Agg.count());

julia> print(render(q, tables = [person]))
SELECT
  "person_1"."year_of_birth",
  count(*) AS "count"
FROM "person" AS "person_1"
GROUP BY "person_1"."year_of_birth"
```

*Number of distinct states among all available locations.*

```jldoctest
julia> location = SQLTable(:location, columns = [:location_id, :state]);

julia> q = From(:location) |>
           Group() |>
           Select(Agg.count_distinct(Get.state));

julia> print(render(q, tables = [location]))
SELECT count(DISTINCT "location_1"."state") AS "count_distinct"
FROM "location" AS "location_1"
```

*For each patient, show the date of their latest visit to a healthcare provider.*

```jldoctest
julia> person = SQLTable(:person, columns = [:person_id]);

julia> visit_occurrence =
           SQLTable(:visit_occurrence, columns = [:visit_occurrence_id, :person_id, :visit_start_date]);

julia> q = From(:person) |>
           LeftJoin(:visit_group => From(:visit_occurrence) |>
                                    Group(Get.person_id),
                    on = (Get.person_id .== Get.visit_group.person_id)) |>
           Select(Get.person_id,
                  :max_visit_start_date =>
                      Get.visit_group |> Agg.max(Get.visit_start_date));

julia> print(render(q, tables = [person, visit_occurrence]))
SELECT
  "person_1"."person_id",
  "visit_group_1"."max" AS "max_visit_start_date"
FROM "person" AS "person_1"
LEFT JOIN (
  SELECT
    max("visit_occurrence_1"."visit_start_date") AS "max",
    "visit_occurrence_1"."person_id"
  FROM "visit_occurrence" AS "visit_occurrence_1"
  GROUP BY "visit_occurrence_1"."person_id"
) AS "visit_group_1" ON ("person_1"."person_id" = "visit_group_1"."person_id")
```

*For each visit, show the number of days passed since the previous visit.*

```jldoctest
julia> visit_occurrence =
           SQLTable(:visit_occurrence, columns = [:visit_occurrence_id, :person_id, :visit_start_date]);

julia> q = From(:visit_occurrence) |>
           Partition(Get.person_id,
                     order_by = [Get.visit_start_date]) |>
           Select(Get.person_id,
                  Get.visit_start_date,
                  :gap => Get.visit_start_date .- Agg.lag(Get.visit_start_date));

julia> print(render(q, tables = [visit_occurrence]))
SELECT
  "visit_occurrence_1"."person_id",
  "visit_occurrence_1"."visit_start_date",
  ("visit_occurrence_1"."visit_start_date" - (lag("visit_occurrence_1"."visit_start_date") OVER (PARTITION BY "visit_occurrence_1"."person_id" ORDER BY "visit_occurrence_1"."visit_start_date"))) AS "gap"
FROM "visit_occurrence" AS "visit_occurrence_1"
```
