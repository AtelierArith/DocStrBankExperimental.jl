```
build_mpc!(m::JuMP.AbstractModel, p::MPCInputs)
```

モデル予測制御モデルのための変数と制約を追加します。カレンダー年1つの代わりに任意の長さのホライズンを持つREoptモデルに似ており、DERのサイズを提供する必要があります。
