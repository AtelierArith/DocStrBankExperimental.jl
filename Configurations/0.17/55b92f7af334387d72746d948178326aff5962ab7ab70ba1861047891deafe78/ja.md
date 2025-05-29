```
from_dict(::Type{OptionType}, ::OptionField{f_name}, ::Type{T}, x) where {OptionType, f_name, T}
```

オプションタイプ `OptionType` に対して、オブジェクト `x` をフィールドタイプ `T` に変換し、フィールド `f_name` に割り当てます。`Base.convert` が例外を発生させた場合は `FieldTypeConversionError` エラーを発生させます。

```
ERROR: MethodError: Cannot `convert` an object of type ...
```
