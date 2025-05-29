```
struct RefDynamic <: TransmissionMode
```

参照動的 `TransmissionMode`。

トラック、船舶、または鉄道輸送などの動的輸送モードの一般的な表現。

# フィールド

  * **`id::String`** は輸送モードの名前/識別子です。
  * **`resource::Resource`** は輸送される資源です。
  * **`trans_cap::TimeProfile`** は輸送モードの容量です。
  * **`trans_loss::TimeProfile`** は輸送中に失われる資源の損失で、比率としてモデル化されています。
  * **`opex_var::TimeProfile`** は輸送されるエネルギー単位あたりの変動運営費です。
  * **`opex_fixed::TimeProfile`** は設置された容量あたりの固定運営費です。
  * **`directions`** は資源が輸送できる方向の数で、1は一方向（A->B）、2は双方向（A<->B）です。
  * **`data::Vector{Data}`** は追加データ（*例*、投資用）です。フィールド `data` はコンストラクタの使用によって条件付きです。
