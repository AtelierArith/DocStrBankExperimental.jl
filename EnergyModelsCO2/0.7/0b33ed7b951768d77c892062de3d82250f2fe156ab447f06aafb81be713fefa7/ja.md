```
CaptureFlueGas{T} <: CaptureData{T}
```

プロキシCO₂インスタンスをキャプチャしますが、エネルギー使用に関連する排出量やプロセス排出量は含まれません。`emissions`を入力として必要としませんが、提供することはできます。

# フィールド

  * **`emissions::Dict{ResourceEmit, T}`** は生産された単位あたりの排出量です。
  * **`co2_capture::Float64`** はCO₂捕集率です。
