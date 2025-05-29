```
Fun(; name, args = [])
Fun(name; args = [])
Fun(name, args...)
Fun.name(args...)
```

SQL関数またはSQL演算子の適用。

`Fun`ノードは、`SQLNode`オブジェクトに対してブロードキャストすることでも生成されます。Julia演算子（`==`, `!=`, `&&`, `||`, `!`）の名前は、それぞれのSQLの同等物（`=`, `<>`, `and`, `or`, `not`）に置き換えられます。

`name`がシンボルのみを含む場合、または`name`が空白で始まるか終わる場合、`Fun`ノードはSQL演算子に変換されます。

`name`が1つ以上の`?`文字を含む場合、それは`?`シンボルが与えられた引数に置き換えられるSQL式のテンプレートとして機能します。リテラル`?`マークを表すには`??`を使用します。SQL式を明確にするために必要な場合は、テンプレートを括弧で囲んでください。

特定の名前は、一般的なSQL関数や演算子を生成するためにカスタマイズされた翻訳を持っています。これらは不規則な構文を持っています：

| `Fun`ノード                   | SQL構文                        |
|:-------------------------- |:---------------------------- |
| `Fun.and(p₁, p₂, …)`       | `p₁ AND p₂ AND …`            |
| `Fun.between(x, y, z)`     | `x BETWEEN y AND z`          |
| `Fun.case(p, x, …)`        | `CASE WHEN p THEN x … END`   |
| `Fun.cast(x, "TYPE")`      | `CAST(x AS TYPE)`            |
| `Fun.concat(s₁, s₂, …)`    | 方言特有、例：`(s₁ \|\| s₂ \|\| …)` |
| `Fun.current_date()`       | `CURRENT_DATE`               |
| `Fun.current_timestamp()`  | `CURRENT_TIMESTAMP`          |
| `Fun.exists(q)`            | `EXISTS q`                   |
| `Fun.extract("FIELD", x)`  | `EXTRACT(FIELD FROM x)`      |
| `Fun.in(x, q)`             | `x IN q`                     |
| `Fun.in(x, y₁, y₂, …)`     | `x IN (y₁, y₂, …)`           |
| `Fun.is_not_null(x)`       | `x IS NOT NULL`              |
| `Fun.is_null(x)`           | `x IS NULL`                  |
| `Fun.like(x, y)`           | `x LIKE y`                   |
| `Fun.not(p)`               | `NOT p`                      |
| `Fun.not_between(x, y, z)` | `x NOT BETWEEN y AND z`      |
| `Fun.not_exists(q)`        | `NOT EXISTS q`               |
| `Fun.not_in(x, q)`         | `x NOT IN q`                 |
| `Fun.not_in(x, y₁, y₂, …)` | `x NOT IN (y₁, y₂, …)`       |
| `Fun.not_like(x, y)`       | `x NOT LIKE y`               |
| `Fun.or(p₁, p₂, …)`        | `p₁ OR p₂ OR …`              |

# 例

*欠損値をN/Aで置き換えます。*

```jldoctest
julia> location = SQLTable(:location, columns = [:location_id, :city]);

julia> q = From(:location) |>
           Select(Fun.coalesce(Get.city, "N/A"));

julia> print(render(q, tables = [location]))
SELECT coalesce("location_1"."city", 'N/A') AS "coalesce"
FROM "location" AS "location_1"
```

*1980年に生まれていない患者を見つけます。*

```jldoctest
julia> person = SQLTable(:person, columns = [:person_id, :year_of_birth]);

julia> q = From(:person) |>
           Where(Get.year_of_birth .!= 1980);

julia> print(render(q, tables = [person]))
SELECT
  "person_1"."person_id",
  "person_1"."year_of_birth"
FROM "person" AS "person_1"
WHERE ("person_1"."year_of_birth" <> 1980)
```

*各患者について、2000年の年齢を表示します。*

```jldoctest
julia> person = SQLTable(:person, columns = [:person_id, :year_of_birth]);

julia> q = From(:person) |>
           Select(Fun."-"(2000, Get.year_of_birth));

julia> print(render(q, tables = [person]))
SELECT (2000 - "person_1"."year_of_birth") AS "_"
FROM "person" AS "person_1"
```

*無効な郵便番号を見つけます。*

```jldoctest
julia> location = SQLTable(:location, columns = [:location_id, :zip]);

julia> q = From(:location) |>
           Select(Fun." NOT SIMILAR TO '[0-9]{5}'"(Get.zip));

julia> print(render(q, tables = [location]))
SELECT ("location_1"."zip" NOT SIMILAR TO '[0-9]{5}') AS "_"
FROM "location" AS "location_1"
```

*郵便番号の最初の3桁を抽出します。*

```jldoctest
julia> location = SQLTable(:location, columns = [:location_id, :zip]);

julia> q = From(:location) |>
           Select(Fun."SUBSTRING(? FROM ? FOR ?)"(Get.zip, 1, 3));

julia> print(render(q, tables = [location]))
SELECT SUBSTRING("location_1"."zip" FROM 1 FOR 3) AS "_"
FROM "location" AS "location_1"
```
