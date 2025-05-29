```julia
StructField(
;
    name,
    data_type,
    default,
    comment,
    needs_conversion,
    exclude_setter,
    valid_range,
    validation_action,
    null_value,
    internal_default
)

```

コード自動生成の目的でStructFieldを構築します。

# 引数

  * `name::String`: フィールド名
  * `data_type::Union{DataType, String}`: フィールドタイプ
  * `default::Any`: 生成されるコンストラクタはこれをデフォルト値として定義します。
  * `comment::String`: フィールド名の上にこのコメントを含めます。デフォルトは空文字列です。
  * `needs_conversion::Bool`: ゲッターおよびセッター関数が単位変換を適用する必要がある場合はtrueに設定します。この組み合わせのコンポーネントタイプとフィールドタイプに対して`get_value(::Component, ::Type)`および`set_value(::Component, ::Type)`を実装する必要があります。
  * `exclude_setter::Bool`: このフィールドのためにセッター関数を生成しないでください。デフォルトはfalseです。
  * `valid_range::Union{Nothing, String, Dict}`: コンポーネントがシステムに追加されるときに範囲検証を有効にします。これを"min"と"max"を持つDictとして定義するか、このフィールドの有効範囲を定義する構造体内のフィールド名を持つStringとして定義します。InfrastructureSystemsはその範囲に対して任意の値を検証します。最大制限がない場合など、適用されない場合は`nothing`を使用します。
  * `validation_action`: これを"error"または"warn"として定義します。"error"の場合、InfrastructureSystemsは検証コードが問題を検出した場合に例外をスローします。それ以外の場合は、警告をログに記録します。
  * `null_value::Any`: フィールドがゼロまたは空であることを示す値、例えばFloat64の場合は0.0です。構造体内のすべてのメンバーがこのフィールドを定義している場合、"demo"コンストラクタが生成されます。これにより、REPLで`val = MyType(nothing)`を入力して、有効な値を気にせずに構造体のレイアウトを確認できます。
  * `internal_default`: デフォルト値を持つ`InfrastructureSystemsInternal`のようなユーザー向けでないフィールドに対してtrueに設定します。
