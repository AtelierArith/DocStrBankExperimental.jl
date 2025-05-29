```
Define(; over; args = [], before = nothing, after = nothing)
Define(args...; over, before = nothing, after = nothing)
```

`Define`ノードは出力列を追加または置き換えます。

デフォルトでは、新しい列は列リストの最後に追加され、置き換えられた列はその位置を保持します。`after = true`（`after = <column>`）を設定すると、新しい列と置き換えられた列の両方が最後に追加されます（指定された列の後）。または、`before = true`（`before = <column>`）を設定すると、新しい列と置き換えられた列の両方が前に追加されます（指定された列の前）。

# 例

*16歳以上の患者を表示します。*

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

*1930年以前に生まれた患者の生年を隠します。*

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
