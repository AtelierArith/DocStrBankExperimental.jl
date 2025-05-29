```
DHPipe
```

2つのノード間のDHパイプ。

# フィールド

  * **`id`** はリンクの名前/識別子です。
  * **`from::Node`** はリンクに流入するノードです。
  * **`to::Node`** はリンクから流出するノードです。
  * **`cap::TimeProfile`** はパイプの熱輸送能力です。
  * **`pipe_length::Float64`** はパイプの長さ（メートル単位）です。
  * **`pipe_loss_factor::Float64`** は熱損失係数（[W m⁻¹ K⁻¹]）です。
  * **`t_ground::TimeProfile`** は地面の温度（°C単位）です。
  * **`resource_heat::ResourceHeat`** はDHPipeによって使用される資源です。
  * **`formulation::Formulation`** はリンクの使用される定式化です。フィールド `formulation` はコンストラクタの使用によって条件付きです。
  * **`data::Vector{<:Data}`** は追加データ（*例*、投資用）です。フィールド `data` はコンストラクタの使用によって条件付きです。
