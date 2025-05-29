```
mangle_symbol_name(oh::ObjectHandle, name::AbstractString)
```

オブジェクト形式特有の命名規則を使用してシンボル名をマングルします。例えば、MachOファイルの場合は `"_"` を接頭辞として付けます。
