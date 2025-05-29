```
from_dict(::Type{OptionType}, ::Type{T}, x) where {OptionType, T}
```

オプション型 `OptionType` に対して、オブジェクト `x` を型 `T` に変換します。これは `Base.convert(::Type{T}, x)` に似ており、定義されていない場合は `Base.convert` にフォールバックします。
