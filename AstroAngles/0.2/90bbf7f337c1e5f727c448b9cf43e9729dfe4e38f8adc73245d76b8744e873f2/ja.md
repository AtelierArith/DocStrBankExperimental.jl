```
parse_dms(input)
```

"deg:arcmin:arcsec" 形式の文字列入力をタプル `(degrees, arcminutes, arcseconds)` に解析します。次の区切り文字はすべて機能し、混在させることができます（最後の区切り文字はオプションです）：

```
"[+-]xx[°d: ]xx['′m: ]xx[\"″s][NESW]"
```

方向が提供されている場合、「S」と「E」は負の値と見なされます（したがって "-1:0:0S" は北に1度です）。
