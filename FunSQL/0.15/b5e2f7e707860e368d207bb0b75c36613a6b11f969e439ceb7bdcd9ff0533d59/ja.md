```
Bind(; over = nothing; args)
Bind(args...; over = nothing)
```

`Bind`ノードは、パラメータを持つクエリを評価します。具体的には、`Bind`は`over`ノードに含まれる[`Var`](@ref)パラメータの値を提供します。

スカラーコンテキストでは、`Bind`ノードは相関サブクエリに変換されます。`Bind`が[`Join`](@ref)ノードの`joinee`ブランチに適用されると、`JOIN LATERAL`クエリに変換されます。

# 例

*少なくとも1回は医療提供者を訪れた患者を表示します。*

```jldoctest
julia> person = SQLTable(:person, columns = [:person_id]);

julia> visit_occurrence = SQLTable(:visit_occurrence, columns = [:visit_occurrence_id, :person_id]);

julia> q = From(:person) |>
           Where(Fun.exists(From(:visit_occurrence) |>
                            Where(Get.person_id .== Var.PERSON_ID) |>
                            Bind(:PERSON_ID => Get.person_id)));

julia> print(render(q, tables = [person, visit_occurrence]))
SELECT "person_1"."person_id"
FROM "person" AS "person_1"
WHERE (EXISTS (
  SELECT "visit_occurrence_1"."visit_occurrence_id"
  FROM "visit_occurrence" AS "visit_occurrence_1"
  WHERE ("visit_occurrence_1"."person_id" = "person_1"."person_id")
))
```

*すべての患者とその最新の医療提供者への訪問日を表示します。*

```jldoctest
julia> person = SQLTable(:person, columns = [:person_id]);

julia> visit_occurrence =
           SQLTable(:visit_occurrence, columns = [:visit_occurrence_id, :person_id, :visit_start_date]);

julia> q = From(:person) |>
           LeftJoin(From(:visit_occurrence) |>
                    Where(Get.person_id .== Var.PERSON_ID) |>
                    Order(Get.visit_start_date |> Desc()) |>
                    Limit(1) |>
                    Bind(:PERSON_ID => Get.person_id) |>
                    As(:visit),
                    on = true) |>
            Select(Get.person_id, Get.visit.visit_start_date);

julia> print(render(q, tables = [person, visit_occurrence]))
SELECT
  "person_1"."person_id",
  "visit_1"."visit_start_date"
FROM "person" AS "person_1"
LEFT JOIN LATERAL (
  SELECT "visit_occurrence_1"."visit_start_date"
  FROM "visit_occurrence" AS "visit_occurrence_1"
  WHERE ("visit_occurrence_1"."person_id" = "person_1"."person_id")
  ORDER BY "visit_occurrence_1"."visit_start_date" DESC
  FETCH FIRST 1 ROW ONLY
) AS "visit_1" ON TRUE
```
