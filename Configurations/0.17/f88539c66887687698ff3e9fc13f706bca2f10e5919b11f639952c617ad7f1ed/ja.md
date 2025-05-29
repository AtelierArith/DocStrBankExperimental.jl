```
from_kwargs(convention!, ::Type{T}; kw...) where T
```

キーワード引数を指定されたオプションタイプ `T` に変換します `convention!` を使用して。詳細は [`from_dict`](@ref) を参照してください。

# 規約

  * `from_underscore_kwargs!`: 同じ名前のサブフィールドを区別するために `_` を使用します。これがデフォルトの動作です。
  * `from_field_kwargs!`: サブフィールドを区別せず、曖昧さがある場合はエラーを返します。
