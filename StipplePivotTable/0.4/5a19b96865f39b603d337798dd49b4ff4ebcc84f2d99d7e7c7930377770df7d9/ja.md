```
フィルター
```

さまざまな属性を持つフィルターを表す可変構造体です。

# フィールド

  * `field::Union{String, Symbol}`: フィルターが適用されるフィールド。
  * `condition::Union{String, Symbol}`: フィールドに適用される条件。
  * `type::Union{String, Symbol, Nothing}`: フィルターのタイプ、デフォルトは `nothing`。
  * `value::Union{Any, Nothing}`: フィルターの値、デフォルトは `nothing`。
  * `selected_values::Union{Any, Vector, Nothing}`: フィルターの選択された値、デフォルトは `nothing`。

# コンストラクタ

  * `Filter(field::Union{String, Symbol}; kwargs...)`: 指定されたフィールドと他の属性のキーワード引数を使用して `Filter` インスタンスを作成します。
