```
Join(; over = nothing, joinee, on, left = false, right = false, optional = false)
Join(joinee; over = nothing, on, left = false, right = false, optional = false)
Join(joinee, on; over = nothing, left = false, right = false, optional = false)
```

`Join`は2つの入力データセットを関連付けます。

`Join`ノードは`JOIN`句を持つクエリに変換されます：

```sql
SELECT ...
FROM $over
JOIN $joinee ON $on
```

結合の種類を指定できます：

  * `INNER JOIN`（デフォルト）；
  * `LEFT JOIN`（`left = true`または[`LeftJoin`](@ref)）；
  * `RIGHT JOIN`（`right = true`）；
  * `FULL JOIN`（`left = true`と`right = true`の両方）；
  * `CROSS JOIN`（`on = true`）。

`optional`が設定されている場合、クエリが`joinee`ブランチの列に依存しない場合は`JOIN`句が省略されます。

ラテラル結合を行うには、`joinee`ブランチに[`Bind`](@ref)を適用します。

出力列の曖昧さを解消するには[`As`](@ref)を使用します。

# 例

*居住州を持つ患者を表示します。*

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
