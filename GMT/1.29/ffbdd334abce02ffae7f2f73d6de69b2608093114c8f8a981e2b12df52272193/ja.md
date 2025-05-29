```
setnodata!(G::GMTgrid, nodata) -> nothing
```

GMTgrid内のすべてのグリッド値をNaNで`nodata`に置き換えます。浮動小数点グリッドのみに作用します。何も返さず、基になる配列を変更します。nodata値を設定することを気にしなかったソースから読み込まれたグリッドを修正するのに便利です（例えば、_FillValueがないnc/hdfグリッドなど）。
