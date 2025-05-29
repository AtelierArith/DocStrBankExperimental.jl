```
update_measurement(client::Client, round::ComputationRound, q, mg, outcome)
```

指定された計算ラウンドと量子ビットの測定を更新します。この関数は、量子ビットに関連付けられたワンタイムパッド整数を取得し、結果とワンタイムパッド整数との絶対差を計算します。

# 引数

  * `client::Client`: 測定が更新されるクライアント。
  * `round::ComputationRound`: 測定が更新される計算ラウンド。
  * `q`: 測定が更新される量子ビット。
  * `mg`: 計算ラウンドに関連付けられた測定グラフ。
  * `outcome`: 測定の結果。

# 戻り値

  * 結果とワンタイムパッド整数との絶対差。

# 例

```julia
client = Client()
round = ComputationRound()
q = 1
mg = MeasurementGraph()
outcome = 0
update_measurement(client, round, q, mg, outcome)
```
