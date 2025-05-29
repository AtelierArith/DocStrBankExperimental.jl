```
set_adduct_name!(nm::AbstractString, adduct::AbstractAdduct)
```

`nm`を`ADDUCTS[:NAME]`によって特定のアダクト文字列を解析するために`adduct`に設定します。

カスタマイズされたアダクトタイプの場合、この関数は`parse_adduct`によって`nm`を`adduct`に解析するために必要です。
