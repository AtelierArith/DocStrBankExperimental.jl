```
search_headwords(dict, keyword)
```

与辞典中给定的 `keyword` 作为词头进行搜索，可以使用繁体或简体字（仅返回词头与 `keyword` 完全匹配的结果；此行为可能在未来版本中更改）。

## 示例

```julia-repl
julia> search_headwords(dict, "2019冠狀病毒病") .|> println;
2019冠狀病毒病 (2019冠状病毒病): [er4 ling2 yi1 jiu3 guan1 zhuang4 bing4 du2 bing4]
        COVID-19, 2019年识别的冠状病毒病
```
