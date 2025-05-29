```
RheoModel(m::RheoModelClass, nt0::NamedTuple)
```

`RheoModel`は、設定されたパラメータを持つレオロジーモデルを表します。これらは、`modelfit`を使用してデータにモデルをフィットさせることによって取得されるか、関連するRheoModelClassを特化させてそのパラメータを指定することによって得られます。パラメータは、名前付きタプルまたはキーワード引数として提供できます。

`RheoModel`オブジェクトは、その後、`modelpredict`を使用して任意の入力に対する応答をシミュレートし、弾性率関数の値にアクセスするために使用できます。

# 例

```@example
julia> model = RheoModel(Maxwell, (k=1, η=2.))
[...]

julia> model = RheoModel(Maxwell, k=1, η=2.)
[...]
```
