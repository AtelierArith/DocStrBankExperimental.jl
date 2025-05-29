```
mutable struct JLKwStruct <: JLExpr
JLKwStruct(;kw...)
```

Typeは、デフォルトのキーワード定義を許可するJuliaの構造体を説明します。この構文は[`JLStruct`](@ref)に似ていますが、フィールドは[`JLKwField`](@ref)型です。

# フィールドとキーワード引数

以下のすべてのフィールドは、コンストラクタのキーワード引数`kw`として有効であり、`<object>.<field>`を介してアクセスできます。

コンストラクタに必要な唯一のキーワード引数は`name`であり、残りはすべてオプションです。

  * `name::Symbol`: 構造体の名前、これは唯一の必須キーワード引数です。
  * `typealias::String`: [`JLKwStruct`](@ref)のエイリアス、また、[Configurations.jl](https://github.com/Roger-luo/Configurations.jl)の`@option`マクロも参照してください。
  * `ismutable::Bool`: 構造体定義が可変かどうか。
  * `typevars::Vector{Any}`: 構造体の型変数、`Symbol`または`Expr`である必要があります。
  * `supertype`: 構造体定義のスーパタイプ。
  * `fields::Vector{JLField}`: 構造体のフィールド定義、[`JLField`](@ref)である必要があります。
  * `constructors::Vector{JLFunction}`: 構造体のコンストラクタ定義、[`JLFunction`](@ref)である必要があります。
  * `line::LineNumberNode`: エラーレポートなどのための定義位置を示す`LineNumberNode`。
  * `doc::String`: 構造体のドキュメンテーション文字列。
  * `misc`: 構造体本体内で発生するその他の事柄、定義上、これは単に通過し、構造体本体の外でそれらを評価するのと同等です。
