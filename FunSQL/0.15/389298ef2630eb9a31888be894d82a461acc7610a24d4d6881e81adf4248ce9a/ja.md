```
Iterate(; over = nothing, iterator)
Iterate(iterator; over = nothing)
```

`Iterate`は、反復クエリの連結出力を生成します。

`over`クエリが最初に評価されます。次に、`iterator`クエリが繰り返し適用されます：`over`の出力に対して、次にその前の実行の出力に対して、そしてそのように続けて、イテレータがデータを生成しなくなるまで続きます。これらすべての出力が連結されて`Iterate`の出力が生成されます。

`iterator`クエリは、`From(^)`表記を使用して前の実行の出力を明示的に参照することができます。

`Iterate`ノードは再帰的共通テーブル式に変換されます：

```sql
WITH RECURSIVE iterator AS (
  SELECT ...
  FROM $over
  UNION ALL
  SELECT ...
  FROM $iterator
)
SELECT ...
FROM iterator
```

# 例

*階乗を計算します。*

```jldoctest
julia> q = Define(:n => 1, :f => 1) |>
           Iterate(From(^) |>
                   Where(Get.n .< 10) |>
                   Define(:n => Get.n .+ 1, :f => Get.f .* (Get.n .+ 1)));

julia> print(render(q))
WITH RECURSIVE "__1" ("n", "f") AS (
  SELECT
    1 AS "n",
    1 AS "f"
  UNION ALL
  SELECT
    ("__2"."n" + 1) AS "n",
    ("__2"."f" * ("__2"."n" + 1)) AS "f"
  FROM "__1" AS "__2"
  WHERE ("__2"."n" < 10)
)
SELECT
  "__3"."n",
  "__3"."f"
FROM "__1" AS "__3"
```

*階乗を計算します。暗黙の`From(^)`を使用します。*

```jldoctest
julia> q = Define(:n => 1, :f => 1) |>
           Iterate(Where(Get.n .< 10) |>
                   Define(:n => Get.n .+ 1, :f => Get.f .* (Get.n .+ 1)));

julia> print(render(q))
WITH RECURSIVE "__1" ("n", "f") AS (
  SELECT
    1 AS "n",
    1 AS "f"
  UNION ALL
  SELECT
    ("__2"."n" + 1) AS "n",
    ("__2"."f" * ("__2"."n" + 1)) AS "f"
  FROM "__1" AS "__2"
  WHERE ("__2"."n" < 10)
)
SELECT
  "__3"."n",
  "__3"."f"
FROM "__1" AS "__3"
```
