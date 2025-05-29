```
rowsmax(zep::Zeppelin, col::Symbol; n::Int=10000000, classname::Union{Missing,AbstractString}=missing)
```

`col`列の`n`個の最大値に関連する行インデックスを返します。

例:

```
# :DAVGによる最大の10個をプロット
plot(zep, rowsmax(zep, :DAVG, 10))
# DAVGでソートされた最も鉄分の多い100のデータ
rowsmax(DataFrame, zep, rowsmax(zep, :FE, 100), sortCol=:DAVG)
```
