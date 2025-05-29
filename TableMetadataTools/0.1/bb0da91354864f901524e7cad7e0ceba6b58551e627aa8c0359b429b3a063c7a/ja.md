```
setcolmetadatastyle!([predicate], table; style::Symbol=:note, [col::Symbol])
```

`table`内の`predicate`に一致する列レベルのキーのスタイルを`style`に設定します。`predicate`が省略された場合、すべてのメタデータが更新されます。`col`が渡された場合、それは列名でなければならず、この列のメタデータのみが更新されます（存在する場合）。

参照: [`setmetadatastyle`!](@ref), [`setallmetadatastyle!](@ref)
