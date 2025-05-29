```
Append(; over = nothing, args)
Append(args...; over = nothing)
```

`Append`は入力データセットを連結します。

すべての入力データセットに存在する列のみが`Append`の出力に含まれます。

`Append`ノードは`UNION ALL`クエリに変換されます：

```sql
SELECT ...
FROM $over
UNION ALL
SELECT ...
FROM $(args[1])
UNION ALL
...
```

# 例

*すべての測定と観察の日付を表示します。*

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
