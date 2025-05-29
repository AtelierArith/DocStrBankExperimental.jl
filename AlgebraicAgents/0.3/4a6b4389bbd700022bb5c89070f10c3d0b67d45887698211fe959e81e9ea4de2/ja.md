```
objective(agent, max_t=Inf)
```

エージェントパラメータの辞書を受け取り、それに対応する解を出力する関数を返します。オプションでシミュレーションのホライズン `max_t` を指定します。

# 例

```julia
o = objective(agent)
o(Dict("agent" => [1., 2.]))
```
