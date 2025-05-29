```
Partition(; over, by = [], order_by = [], frame = nothing, name = nothing)
Partition(by...; over, order_by = [], frame = nothing, name = nothing)
```

`Partition`ノードは隣接する行を関連付けます。

具体的には、`Partition`は同じデータセット内の各行を隣接する行にどのように関連付けるかを指定します。行は指定されたキーで`by`パーティションされ、各パーティション内で`order_by`キーを使用して順序付けられます。パラメータ`frame`は関連する行の範囲をカスタマイズします。これらの関連する行は、`Partition`の出力に適用される集約関数[`Agg`](@ref)によって要約されます。オプションのパラメータ`name`は、パーティションを保持するフィールドを指定します。

`Partition`ノードは`WINDOW`句を持つクエリに変換されます：

```sql
SELECT ...
FROM $over
WINDOW w AS (PARTITION BY $by... ORDER BY $order_by...)
```

# 例

*患者の訪問を列挙します。*

```jldoctest
julia> visit_occurrence =
           SQLTable(:visit_occurrence, columns = [:visit_occurrence_id, :person_id, :visit_start_date]);

julia> q = From(:visit_occurrence) |>
           Partition(Get.person_id, order_by = [Get.visit_start_date]) |>
           Select(Agg.row_number(), Get.visit_occurrence_id);

julia> print(render(q, tables = [visit_occurrence]))
SELECT
  (row_number() OVER (PARTITION BY "visit_occurrence_1"."person_id" ORDER BY "visit_occurrence_1"."visit_start_date")) AS "row_number",
  "visit_occurrence_1"."visit_occurrence_id"
FROM "visit_occurrence" AS "visit_occurrence_1"
```

明示的なパーティション名を使用した同じ例。

```jldoctest
julia> visit_occurrence =
           SQLTable(:visit_occurrence, columns = [:visit_occurrence_id, :person_id, :visit_start_date]);

julia> q = From(:visit_occurrence) |>
           Partition(Get.person_id, order_by = [Get.visit_start_date], name = :visit_by_person) |>
           Select(Get.visit_by_person |> Agg.row_number(), Get.visit_occurrence_id);

julia> print(render(q, tables = [visit_occurrence]))
SELECT
  (row_number() OVER (PARTITION BY "visit_occurrence_1"."person_id" ORDER BY "visit_occurrence_1"."visit_start_date")) AS "row_number",
  "visit_occurrence_1"."visit_occurrence_id"
FROM "visit_occurrence" AS "visit_occurrence_1"
```

*生年ごとの患者数の移動平均を計算します。*

```jldoctest
julia> person = SQLTable(:person, columns = [:person_id, :year_of_birth]);

julia> q = From(:person) |>
           Group(Get.year_of_birth) |>
           Partition(order_by = [Get.year_of_birth],
                     frame = (mode = :range, start = -1, finish = 1)) |>
           Select(Get.year_of_birth, Agg.avg(Agg.count()));

julia> print(render(q, tables = [person]))
SELECT
  "person_1"."year_of_birth",
  (avg(count(*)) OVER (ORDER BY "person_1"."year_of_birth" RANGE BETWEEN 1 PRECEDING AND 1 FOLLOWING)) AS "avg"
FROM "person" AS "person_1"
GROUP BY "person_1"."year_of_birth"
```
