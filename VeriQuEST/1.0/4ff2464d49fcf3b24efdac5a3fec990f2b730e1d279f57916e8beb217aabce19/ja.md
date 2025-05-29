```
update_measurement(client::Client, q, mg, outcome)
```

この関数は、測定グラフからラウンドタイプを取得し、その後、クライアント、ラウンドタイプ、キュービット、測定グラフ、および結果を引数として`update_measurement`関数を呼び出します。

# 引数

  * `client::Client`: 測定が更新されるクライアント。
  * `q`: 測定が更新されるキュービット。
  * `mg`: 計算ラウンドに関連する測定グラフ。
  * `outcome`: 測定の結果。

# 戻り値

  * クライアント、ラウンドタイプ、キュービット、測定グラフ、および結果を使って`update_measurement`を呼び出した結果。

# 例

```julia
client = Client()
q = 1
mg = MeasurementGraph()
outcome = 0
update_measurement(client, q, mg, outcome)
```
