```
dyn_entry_is_string(d::ELFDynEntry)
```

与えられた `ELFDynEntry` が動的文字列テーブル内のオフセットを表す場合、`true` を返します。したがって、`strtab_lookup()` で使用できます。
