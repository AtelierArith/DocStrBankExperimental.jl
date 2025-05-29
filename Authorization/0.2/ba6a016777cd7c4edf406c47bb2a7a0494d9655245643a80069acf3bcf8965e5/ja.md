必須フィールド：

  * id::String;
  * id2permission::Dict{String, Permission};        # リソースID => パーミッション
  * idpattern2permission::Dict{Regex, Permission};  # リソースIDパターン => パーミッション
  * type2permission::Dict{DataType, Permission};    # リソースタイプ => パーミッション
