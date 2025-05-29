```
setparameters!(agent, parameters)
```

エージェントのパラメータを設定します。パラメータは、`path => params` ペアを含む辞書の形式で受け入れられます。

# 例

```julia
setparameters!(agent, Dict("agent1/agent2" => Dict(:α=>1)))
```
