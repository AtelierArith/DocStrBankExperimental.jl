```
parse_adduct(::AbstractString) -> AbstractAdduct
```

文字列を `AbstractAdduct` に解析します。この関数は最初に `ELEMENTS[:NAME]` で文字列を検索し、その後入力文字列を分解して `PosAdduct` または `NegAdduct` を構築します。
