```
get_pedigree(pedfile::AbstractString;header=false,separator=',',missingstrings=["0"])
```

  * **ヘッダー**（デフォルトは`false`）、**区切り文字**（デフォルトは`,`）、および欠損値（デフォルトは["0"]）を指定して、系譜ファイルから系譜情報を取得します。
  * 系譜ファイルのフォーマット：

```
a,0,0
c,a,b
d,a,c
```
