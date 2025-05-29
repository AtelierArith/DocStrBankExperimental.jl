```
rowsmin(zep::Zeppelin, col::Symbol; n::Int=10000000, classname::Union{Missing,AbstractString}=missing)
```

`col`列に関連する`n`個の最小値の行インデックスを返します。

例:

```
# :DAVGによる10個の最小値をプロット
plot(zep, rowsmin(zep, :DAVG, 10))
# DAVGでソートされた100個の最も鉄分の多いデータ
rowsmin(DataFrame, zep, rowsmax(zep, :FE, 100), sortCol=:DAVG)
```
