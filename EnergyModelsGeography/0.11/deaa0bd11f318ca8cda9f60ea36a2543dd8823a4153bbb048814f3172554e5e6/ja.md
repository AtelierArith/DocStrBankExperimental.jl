```
struct RefStatic <: TransmissionMode
```

参照静的 `TransmissionMode`。

静的伝送モードの一般的な表現、例えば、架空の電力線やパイプラインなど。

# フィールド

  * **`id::String`** は伝送モードの名前/識別子です。
  * **`resource::Resource`** は輸送される資源です。
  * **`trans_cap::Real`** は伝送モードの容量です。
  * **`trans_loss::Real`** は伝送中に輸送される資源の損失で、比率としてモデル化されています。
  * **`opex_var::TimeProfile`** は輸送されるエネルギー単位あたりの変動運営費です。
  * **`opex_fixed::TimeProfile`** は設置容量あたりの固定運営費です。
  * **`directions`** は資源が輸送できる方向の数で、1は一方向（A->B）、2は双方向（A<->B）です。
  * **`data::Vector{Data}`** は追加データ（*例*、投資用）です。フィールド `data` はコンストラクタの使用によって条件付きです。
