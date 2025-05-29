```
get_parameters(agent::Agent, target_param::Union{String,Tuple})
```

エージェントから単一のパラメータを取得します。単一の値を返します。

```
get_parameters(agent::Agent, target_param::Vector)
```

エージェントから一連のパラメータ値を取得します。パラメータとその値の辞書を返します。

```
get_parameters(agent::Agent)
```

エージェントからすべてのパラメータを取得します。パラメータとその値の辞書を返します。
