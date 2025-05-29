```
update_measurement(client::Client, round::Union{MBQC, TestRound}, q, mg, outcome)
```

この関数は、測定ベースの量子計算（MBQC）またはテストラウンドの文脈で使用されます。結果を受け取り、単にそれを変更せずに返します。

# 引数

  * `client::Client`: 測定が更新されるクライアント。
  * `round::Union{MBQC, TestRound}`: 計算ラウンドがMBQCの一部であるかテストラウンドであるかを指定します。
  * `q`: 測定が更新される量子ビット。
  * `mg`: 計算ラウンドに関連する測定グラフ。
  * `outcome`: 測定の結果。

# 戻り値

  * 引数として渡されたのと同じ`outcome`。

# 例

```julia
client = Client()
round = MBQC()
q = 1
mg = MeasurementGraph()
outcome = 0
update_measurement(client, round, q, mg, outcome)
```
