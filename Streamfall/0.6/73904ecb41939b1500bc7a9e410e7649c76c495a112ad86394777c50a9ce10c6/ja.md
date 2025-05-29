```
run_node!(
    node::DamNode,
    ts::Int64,
    rain::Float64,
    et::Float64,
    volume::Float64,
    inflow::Float64,
    extractions::Float64,
    gw_flux::Float64
)
```

ダムノードの単一時間ステップの流出を計算します。

# 引数

  * `node` : DamNode
  * `rain` : 降雨量（mm）
  * `et` : 蒸発散データ（mm）
  * `irrig_ext` : 灌漑抽出量
  * `extractions` : 抽出データ（ML）
  * `gw_flux` : 地下水相互作用

# 戻り値

ダムからの流出
