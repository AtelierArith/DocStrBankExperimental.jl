```
getagent(agent::AbstractAlgebraicAgent, path::Union{Glob.FilenameMatch, Regex})
```

正規表現またはグロブ文字列を指定してエージェントを取得します。

## 例

```julia
getagent(a, r"agent.*")
getagent(a, glob"**/agent/")
```
