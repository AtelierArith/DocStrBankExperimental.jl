```
mangle_section_name(oh::ObjectHandle, name::AbstractString)
```

セクション `name` をオブジェクト形式特有の命名規則に変換します。例えば、`ELF`/`COFF` ファイルの場合は `".bss"` を返し、`MachO` ファイルの場合は `"__bss"` を返します。
