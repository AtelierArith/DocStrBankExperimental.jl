```julia
struct VariableDFG <: DistributedFactorGraphs.AbstractDFGVariable
```

変数情報は、jsonを使用して多言語に対応する形でパッケージ化されています。

注意:

  * タイムスタンプはUTCの`ZonedDateTime`です。
  * nstimeはミッション時間として使用でき、タイムスタンプのミリ秒がミッション開始のnstimeと一致するという慣例があります。

      * 例: タイムスタンプが`2020-01-01 06:30:01.250 UTC`で、最初のnstimeが`250_000_000`です。
