必要なフィールド：

  * id::String;                                     # Authorization.AbstractClientから
  * id2permission::Dict{String, Permission};        # リソースID => パーミッション（Authorization.AbstractClientから）
  * idpattern2permission::Dict{Regex, Permission};  # リソースIDパターン => パーミッション（Authorization.AbstractClientから）
  * type2permission::Dict{DataType, Permission};    # リソースタイプ => パーミッション（Authorization.AbstractClientから）
  * rootbucketID::String  # ルートバケットのID       # ObjectStoresに特有
