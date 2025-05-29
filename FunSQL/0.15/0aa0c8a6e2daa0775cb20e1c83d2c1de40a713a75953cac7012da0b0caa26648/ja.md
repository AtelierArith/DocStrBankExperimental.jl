```
Select(; over; args)
Select(args...; over)
```

`Select`ノードは出力列を指定します。

```sql
SELECT $args...
FROM $over
```

列ラベルを[`As`](@ref)で設定します。

# 例

*患者のIDと年齢をリストします。*

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
