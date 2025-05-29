```
struct PipeSimple <: PipeMode
```

この `TransmissionMode` は、輸送される `Resource` を変更することを可能にします。

これの使用例としては、*e.g.*、フィールド 'pressure' を持つ `Resource` のサブタイプ構造体を定義することが挙げられます。この PipelineMode は、入口で圧力 p₁ を持つ `SomeSubtype<:Resource` を受け入れ、出口で圧力 p₂ を持つことができます。

このタイプは、輸送される `Resource` の体積に比例して資源を消費することもサポートしています（入口で）。これは、パイプラインを運営するために必要な電力をモデル化するために使用される可能性があります。

`PipeSimple` を使用したパイプライン輸送は、一方向であると想定されています。消費する資源がこの場合、間違った `Area` で消費されるため、双方向輸送に `PipeSimple` を使用することはできません。

# フィールド

  * **`id::String`** は、印刷された出力で使用される識別子です。
  * **`inlet::Resource`** は、輸送に入る `Resource` です。
  * **`outlet::Resource`** は、輸送の出口から出る `Resource` です。
  * **`consuming::Resource`** は、運営によって消費される `Resource` です。
  * **`consumption_rate::TimeProfile`** は、リソース `Pipeline.consuming` が消費される割合で、入口に入るリソースの体積の比率として表されます、*i.e.*:

    ```
      `consumption_rate` = 消費された体積 / 入口の体積 (運営期間あたり)
    ```
  * **`trans_cap::Real`** は、輸送モードの容量です。
  * **`trans_loss::Real`** は、輸送中に失われる資源の割合としてモデル化された輸送資源の損失です。
  * **`opex_var::TimeProfile`** は、輸送されるエネルギー単位あたりの変動運営費用です。
  * **`opex_fixed::TimeProfile`** は、設置された容量あたりの固定運営費用です。
  * **`data::Vector{Data}`** は、追加データ (*e.g.*、投資用) です。フィールド `data` は、コンストラクタの使用によって条件付きです。
