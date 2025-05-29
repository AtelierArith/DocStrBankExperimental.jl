```
parse_comparison(s) -> comp
```

文字列 `s` を解析して、テーブルをフィルタリングするための比較を取得します。

解析する文字列 `s` の可能な例：

  * `"nation=>narnia"` - row.nation=="narnia" のすべての行
  * `"bus_idx=>5"` - row.bus_idx==5 のすべての行
  * `"year_on=>(y2002,y2030)"` - `row.year_on` が2002年から2030年の間にあるすべての行（両端を含む）。
  * `"emis_co2=>(0.0,4.99)"` - `row.emis_co2` が0.0から4.99の間にあるすべての行（両端を含む）。 （整数や負の数にも対応）
  * `"emis_co2=> >(0)"` - `row.emis_co2` が0より大きいすべての行（整数や負の数にも対応）
  * `"year_on=> >(y2002)"` - `row.year_on` が "y2002" より大きいすべての行（"y2002.4" のような小数年にも対応）
  * `"genfuel=>[ng, wind, solar]"` - `row.genfuel` が "ng"、"wind"、または "solar" であるすべての行。整数や浮動小数点数にも対応。
  * `"genfuel=>![ng, coal, biomass]"` - `row.genfuel` が "ng"、"coal"、または "biomass" でないすべての行。整数や浮動小数点数にも対応。
