```
build_mpc!(m::JuMP.AbstractModel, p::MPCInputs)
```

モデル予測制御モデルのための変数と制約を追加します。カレンダー年1年ではなく、任意の長さのホライズンを持つREoptモデルに似ています。また、DERのサイズを提供する必要があります。
