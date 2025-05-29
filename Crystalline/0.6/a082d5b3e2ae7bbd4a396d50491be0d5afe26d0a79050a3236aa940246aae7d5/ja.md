```
conventionalize(op′::SymOperation, cntr::Char, modw::Bool=true) --> typeof(op)
```

従来の設定での対称操作 `op` $= \{W|w\}$ を、原始的設定での入力対称操作 `op′` $≡ \{W'|w'\}$ から変換します。

センタリング引数 `cntr` とオプション引数 `modw` の説明については、[`primitivize(::SymOperation, ::Char, ::Bool)`](@ref) を参照してください。
