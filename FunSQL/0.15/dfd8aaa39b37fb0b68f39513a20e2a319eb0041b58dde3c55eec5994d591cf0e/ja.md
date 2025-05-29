```
As(; over = nothing, name)
As(name; over = nothing)
name => over
```

スカラーコンテキストでは、`As`は出力列の名前を指定します。タブularデータに適用されると、`As`はデータをネストされたレコードでラップします。

矢印演算子（`=>`）は`As`の省略表記です。

# 例

*すべての患者IDを表示します。*

```jldoctest
julia> person = SQLTable(:person, columns = [:person_id, :year_of_birth]);

julia> q = From(:person) |> Select(:id => Get.person_id);

julia> print(render(q, tables = [person]))
SELECT "person_1"."person_id" AS "id"
FROM "person" AS "person_1"
```

*すべての患者とその居住州を表示します。*

```jldoctest
julia> person = SQLTable(:person, columns = [:person_id, :year_of_birth, :location_id]);

julia> location = SQLTable(:location, columns = [:location_id, :state]);

julia> q = From(:person) |>
           Join(From(:location) |> As(:location),
                on = Get.location_id .== Get.location.location_id) |>
           Select(Get.person_id, Get.location.state);

julia> print(render(q, tables = [person, location]))
SELECT
  "person_1"."person_id",
  "location_1"."state"
FROM "person" AS "person_1"
JOIN "location" AS "location_1" ON ("person_1"."location_id" = "location_1"."location_id")
```
