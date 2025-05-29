```
From(; source)
From(tbl::SQLTable)
From(name::Symbol)
From(^)
From(df)
From(f::SQLNode; columns::Vector{Symbol})
From(::Nothing)

`From`はデータベーステーブルの内容を出力します。

パラメータ`source`は次のいずれかである可能性があります：

  * [`SQLTable`](@ref)オブジェクト;
  * `Symbol`値;
  * `^`オブジェクト;
  * `DataFrame`またはTables.jl互換のデータセット;
  * テーブル値関数を表す`SQLNode`。この場合、`From`は関数によって生成される出力列のリストを持つキーワードパラメータ`columns`も必要です。
  * `nothing`。

`source`がシンボルの場合、[`SQLCatalog`](@ref)内のテーブルまたは[`With`](@ref)ノードで定義された中間データセットを参照できます。

`From`ノードは`FROM`句を持つSQLクエリに変換されます：

```

sql SELECT ... FROM :source

```

`From(^)`は[`Iterate`](@ref)のコンポーネントでなければなりません。[`Iterate`](@ref)の文脈では、前の反復の出力を指します。

`From(::DataFrame)`は`VALUES`句に変換されます。

`From(nothing)`は1行で列がないデータセットを出力し、通常は省略可能です。

# 例

*すべての患者をリストします。*

```

jldoctest julia> person = SQLTable(:person, columns = [:person*id, :year*of_birth]);

julia> q = From(person);

julia> print(render(q)) SELECT   "person*1"."person*id",   "person*1"."year*of*birth" FROM "person" AS "person*1"

```

*すべての患者をリストします。*

```

jldoctest julia> person = SQLTable(:person, columns = [:person*id, :year*of_birth]);

julia> q = From(:person);

julia> print(render(q, tables = [person])) SELECT   "person*1"."person*id",   "person*1"."year*of*birth" FROM "person" AS "person*1"

```

*本態性高血圧と診断されたすべての患者を表示します。*

```

jldoctest julia> person = SQLTable(:person, columns = [:person*id, :year*of_birth]);

julia> condition*occurrence =            SQLTable(:condition*occurrence,                     columns = [:condition*occurrence*id, :person*id, :condition*concept_id]);

julia> q = From(:person) |>            Where(Fun.in(Get.person*id, From(:essential*hypertension) |>                                        Select(Get.person*id))) |>            With(:essential*hypertension =>                     From(:condition*occurrence) |>                     Where(Get.condition*concept_id .== 320128));

julia> print(render(q, tables = [person, condition*occurrence])) WITH "essential*hypertension*1" ("person*id") AS (   SELECT "condition*occurrence*1"."person*id"   FROM "condition*occurrence" AS "condition*occurrence*1"   WHERE ("condition*occurrence*1"."condition*concept*id" = 320128) ) SELECT   "person*1"."person*id",   "person*1"."year*of*birth" FROM "person" AS "person*1" WHERE ("person*1"."person*id" IN (   SELECT "essential*hypertension*2"."person*id"   FROM "essential*hypertension*1" AS "essential*hypertension_2" ))

```

*現在の日付を表示します。*

```

jldoctest julia> q = From(nothing) |>            Select(Fun.current_date());

julia> print(render(q)) SELECT CURRENT*DATE AS "current*date"

julia> q = Select(Fun.current_date());

julia> print(render(q)) SELECT CURRENT*DATE AS "current*date"

```

`DataFrame`をクエリします。

```

jldoctest julia> df = DataFrame(name = ["SQL", "Julia", "FunSQL"],                       year = [1974, 2012, 2021]);

julia> q = From(df) |>            Group() |>            Select(Agg.min(Get.year), Agg.max(Get.year));

julia> print(render(q)) SELECT   min("values*1"."year") AS "min",   max("values*1"."year") AS "max" FROM (   VALUES     (1974),     (2012),     (2021) ) AS "values_1" ("year")

```

カンマ区切りの数字を解析します。

```

jldoctest julia> q = From(Fun.regexp_matches("2,3,5,7,11", "(\d+)", "g"),                 columns = [:captures]) |>            Select(Fun."CAST(?[1] AS INTEGER)"(Get.captures));

julia> print(render(q, dialect = :postgresql)) SELECT CAST("regexp*matches*1"."captures"[1] AS INTEGER) AS "*" FROM regexp*matches('2,3,5,7,11', '(\d+)', 'g') AS "regexp*matches*1" ("captures") ```
