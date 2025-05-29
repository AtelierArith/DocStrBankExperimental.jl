```
function image_pass!(jump_model::JuMP.Model, input::Array{Float32, 4}, cnnstruct::CNNStructure, layer::Int)
```

**デバッグバージョン**

畳み込みニューラルネットワークを表すJuMPモデルを通して画像をフォワードパスします。

入力として与えられたインデックスのレイヤーの出力を返します。
