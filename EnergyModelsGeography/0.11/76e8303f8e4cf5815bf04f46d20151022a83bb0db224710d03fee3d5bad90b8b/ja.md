```
struct PipeLinepackSimple <: PipeMode
```

ラインパッキングを単純なストレージ機能として実装したパイプラインモデル。

# フィールド

  * **`id::String`** は印刷出力で使用される識別子です。
  * **`inlet::Resource`** は送信に入る `Resource` です。
  * **`outlet::Resource`** は送信の出口から出る `Resource` です。
  * **`consuming::Resource`** は送信が操作によって消費する `Resource` です。
  * **`consumption_rate::TimeProfile`** はリソース `Pipeline.consuming` が消費される割合で、入口に入るリソースの体積の比率として表されます。すなわち：

    ```
      `consumption_rate` = 消費された体積 / 入口の体積 (運用期間あたり)
    ```
  * **`trans_cap::Real`** は送信モードの容量です。
  * **`trans_loss::Real`** は送信中に輸送されるリソースの損失で、比率としてモデル化されています。
  * **`opex_var::TimeProfile`** は輸送されるエネルギー単位あたりの変動運営費用です。
  * **`opex_fixed::TimeProfile`** は設置された容量あたりの固定運営費用です。
  * **`energy_share::Float64`** はパイプライン容量に対するストレージエネルギー容量です。
  * **`data::Array{<:Data}`** は追加データ (*e.g.*, 投資用) です。フィールド `data` はコンストラクタの使用によって条件付きです。
