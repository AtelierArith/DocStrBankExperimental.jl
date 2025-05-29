```
xml(survey::Survey)
```

`Survey`オブジェクトからXMLドキュメントを構築します。

# 例

```julia-repl
julia> s = survey(100000, "my survey")
julia> xml(s)
```
