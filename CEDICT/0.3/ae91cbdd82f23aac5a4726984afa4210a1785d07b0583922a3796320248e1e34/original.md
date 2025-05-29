```
search_headwords(dict, keyword)
```

Search for the given `keyword` in the dictionary as a headword, in either traditional or simplified characters (will only return results where the headword is an exact match for `keyword`; this behavior may change in future releases).

## Examples

```julia-repl
julia> search_headwords(dict, "2019冠狀病毒病") .|> println;
2019冠狀病毒病 (2019冠状病毒病): [er4 ling2 yi1 jiu3 guan1 zhuang4 bing4 du2 bing4]
        COVID-19, the coronavirus disease identified in 2019
```
