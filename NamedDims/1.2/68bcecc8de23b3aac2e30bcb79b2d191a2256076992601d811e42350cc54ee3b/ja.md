```
rename(nda::NamedDimsArray, names)
rename(nda::NamedDimsArray, pairs)
```

指定された次元の `names` または `pairs` の `old=>new` 名を持つ新しい `NamedDimsArray` を返します。 `rename` は名前を完全に置き換えますが、同じバックアレイをラップし続けます。コンストラクタとは異なり、新しい名前が古い名前と互換性がある必要はありません（ただし、次元の数を一致させる必要があります）。
