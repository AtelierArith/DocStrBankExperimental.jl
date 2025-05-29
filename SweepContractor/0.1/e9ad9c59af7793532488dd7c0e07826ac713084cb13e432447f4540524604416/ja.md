```
sweep_contract_dangling(LTN::LabelledTensorNetwork, χ, τ;
    fast=false, valid=false, planar=false, connected=false, report=false)
sweep_contract_dangling(TN::TensorNetwork, χ, τ;
    fast=false, valid=false, planar=false, connected=false, report=false)
```

ダングリングレッグを持つオープンテンソルネットワークを評価するために使用できる`sweep_contract`の修正版です。これは、最終テンソルが収束する前にスイープ手順を停止し、これまでのネットワークを近似するMPSを返すことによって行われます。これを行うためには、ネットワーク内に他の部分の上に位置するダミーテンソルが存在する必要があります。つまり、y座標が高い必要があります。

`sweep_contract`と同様に、アンダーフロー/オーバーフローの問題は、MPSを浮動小数点形式で返すことによって回避されます。出力はタプル`(mps::MPS, i::Int64)`として返され、`mps`は[1,2)の2ノルムを持ち、MPS `mps*2^i`を表します。

その他の詳細については、`sweep_contract`のドキュメントを参照してください。
