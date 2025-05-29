```
create_departure(data,F = 1.0;verbose = false)
```

`EmpiricDeparture`を使用した`MultiFluid`モデルのための出発モデルを作成します。

`data`が`String`であり、`{`または`[`で始まる場合、それはJSONテキストとして認識されます。それ以外の場合、テキストはファイルの場所として解析されます。JSON解析をスキップしたい場合は、`Dict`または`NamedTuple`を渡すことができます。

## 例

```julia
d1 = create_departure("/data/EthanePropane.json",0.9) # ファイルから読み込み

dep = Dict(
    #縮小されたCoolProp出発形式、タイプとパラメータのみが必要です。
    #ResidualHelmholtzPowerも機能します。
    :type => "Exponential",
    :n => [1,1,1,1],
    :t => [1,1,1,1],
    :d => [1,1,1,1],
    :l => [1,1,1,1],
)

d2 = create_departure(dep) #Fは1.0に設定されています
```
