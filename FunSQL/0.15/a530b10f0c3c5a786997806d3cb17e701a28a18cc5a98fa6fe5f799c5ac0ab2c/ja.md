```
Group(; over, by = [], sets = sets, name = nothing)
Group(by...; over, sets = sets, name = nothing)
```

`Group`ノードは入力データセットを要約します。

具体的には、`Group`は指定されたグルーピングキーのすべてのユニークな値を出力します。このキーは、入力行を互いに重ならないグループに分割し、`Group`の出力に適用される集約関数[`Agg`](@ref)によって要約されます。パラメータ`sets`は、グルーピングモードインジケーター`:cube`または`:rollup`を使用するか、明示的に`Vector{Vector{Symbol}}`として指定されたグルーピングセットを指定します。オプションのパラメータ`name`は、グループを保持するフィールドを指定します。

`Group`ノードは、`GROUP BY`句を持つSQLクエリに変換されます：

```sql
SELECT ...
FROM $over
GROUP BY $by...
```

# 例

*患者の総数。*

```jldoctest
julia> person = SQLTable(:person, columns = [:person_id, :year_of_birth]);

julia> q = From(:person) |>
           Group() |>
           Select(Agg.count());

julia> print(render(q, tables = [person]))
SELECT count(*) AS "count"
FROM "person" AS "person_1"
```

*出生年ごとの患者数。*

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

明示的なグループ名を使用した同じ例。

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

*出生年ごとの患者数と患者の総数。*

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

*すべての利用可能な場所における異なる州。*

```jldoctest
julia> location = SQLTable(:location, columns = [:location_id, :state]);

julia> q = From(:location) |>
           Group(Get.state);

julia> print(render(q, tables = [location]))
SELECT DISTINCT "location_1"."state"
FROM "location" AS "location_1"
```
