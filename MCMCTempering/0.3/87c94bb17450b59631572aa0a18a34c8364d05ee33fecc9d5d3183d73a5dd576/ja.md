```
TemperedSampler <: AbstractMCMC.AbstractSampler
```

`TemperedSampler`構造体は、Parallel Temperingアルゴリズムを適用するためのサンプラーをラップします。

# フィールド

  * `sampler`: 温度分布をターゲットにするために使用されるサンプラー
  * `chain_to_beta`: 逆温度βのコレクション; β[i]はi番目の温度モデルに対応します
  * `swapstrategy`: スワッピングに使用する戦略
  * `adapt`: 適応するかどうかを指定するブールフラグ
  * `adaptation_states`: 適応パラメータ
