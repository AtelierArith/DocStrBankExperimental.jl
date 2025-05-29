```
Group(; over, by = [], sets = sets, name = nothing)
Group(by...; over, sets = sets, name = nothing)
```

The `Group` node summarizes the input dataset.

Specifically, `Group` outputs all unique values of the given grouping key. This key partitions the input rows into disjoint groups that are summarized by aggregate functions [`Agg`](@ref) applied to the output of `Group`.  The parameter `sets` specifies the grouping sets, either with grouping mode indicators `:cube` or `:rollup`, or explicitly as `Vector{Vector{Symbol}}`. An optional parameter `name` specifies the field to hold the group.

The `Group` node is translated to a SQL query with a `GROUP BY` clause:

```sql
SELECT ...
FROM $over
GROUP BY $by...
```

# Examples

*Total number of patients.*

```jldoctest
julia> person = SQLTable(:person, columns = [:person_id, :year_of_birth]);

julia> q = From(:person) |>
           Group() |>
           Select(Agg.count());

julia> print(render(q, tables = [person]))
SELECT count(*) AS "count"
FROM "person" AS "person_1"
```

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

The same example using an explicit group name.

```jldoctest
julia> person = SQLTable(:person, columns = [:person_id, :year_of_birth]);

julia> q = From(:person) |>
           Group(Get.year_of_birth, name = :person) |>
           Select(Get.year_of_birth, Get.person |> Agg.count());

julia> print(render(q, tables = [person]))
SELECT
  "person_1"."year_of_birth",
  count(*) AS "count"
FROM "person" AS "person_1"
GROUP BY "person_1"."year_of_birth"
```

*Number of patients per year of birth and the total number of patients.*

```jldoctest
julia> person = SQLTable(:person, columns = [:person_id, :year_of_birth]);

julia> q = From(:person) |>
           Group(Get.year_of_birth, sets = :cube) |>
           Select(Get.year_of_birth, Agg.count());

julia> print(render(q, tables = [person]))
SELECT
  "person_1"."year_of_birth",
  count(*) AS "count"
FROM "person" AS "person_1"
GROUP BY CUBE("person_1"."year_of_birth")
```

*Distinct states across all available locations.*

```jldoctest
julia> location = SQLTable(:location, columns = [:location_id, :state]);

julia> q = From(:location) |>
           Group(Get.state);

julia> print(render(q, tables = [location]))
SELECT DISTINCT "location_1"."state"
FROM "location" AS "location_1"
```
