```
render_template(template locale) :: String
render_template(template, reference_dfrow; locale) :: String
```

与えられた事前定義されたテンプレートを、`template`をトークンに分割することで具現化します。各トークンは、Impostorによってエクスポートされた生成関数に関連付けられている*可能性があります*。生成関数に関連付けられたトークンは、その生成関数の対応物と正確に同じ綴りであることが期待されます（*例*：トークン "address" は生成関数 `address` に関連付けられています）。

実用的な理由から、Impostorによってエクスポートされていないトークン（以下の例を参照）は、具現化されたテンプレートにそのまま繰り返されます。これは、Impostorが誤って綴られた生成関数と、具現化されたテンプレートに存在すべき生のテキストを区別することができないためです。

オプションとして、`template`内のトークンによって参照される可能性のある列名を持つ`reference_dfrow`を提供します。これは、階層データ操作の文脈で便利です。

# パラメータ

  * `template::String`: 具現化されるテンプレート。
  * `reference_dfrow::DataFrames.DataFrameRow`: 単一行のDataFrame（`DataFrameRow`）に格納された参照値；値へのアクセスは`reference_dfrow`の列名への参照を通じて行われます（以下の例を参照）。

# 例

## 文字列の具現化

```@repl
julia> template = "firstname surname occupation";

julia> render_template(template; locale="en_US")
"Charles Fraser Anthropologyst"

julia> template = "I know firstname surname, this person is a(n) occupation";

julia> render_template(template; locale="en_US")
"I know Charles Jameson, this person is a(n) Mathematician"
```

## 欠落トークン

```@repl
julia> template = "firstname lastname"  # 'lastname' 関数は存在しないことに注意
"firstname lastname"

julia> render_template(template; locale="en_US")
"Kate lastname"
```

## `DataFrameRow`の使用

```@repl
julia> dfrow = DataFrame(state="California", city="San Francisco")[1, :]
1×2 DataFrame
 Row │ state       city
     │ String      String
─────┼───────────────────────────
   1 │ California  San Francisco

julia> template = "I live in city (state)"

julia> render_template(template, dfrow; locale = "en_US")
"I live in San Francisco (California)"
```
