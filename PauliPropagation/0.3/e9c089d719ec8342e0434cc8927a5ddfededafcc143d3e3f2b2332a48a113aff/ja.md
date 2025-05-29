```
propagate(circ, psum::PauliSum{PauliStringType,NodePathProperties}; max_weight=Inf, max_freq=Inf, max_sins=Inf, customtruncfunc=nothing, kwargs...)
```

回路 `circ` を通じて伝播された `PauliSum` の Pauli 伝播サロゲートを構築します。回路は `CliffordGate` と `PauliRotation` のみを含む必要があります。これは Pauli 和に逆順で適用され、各ゲートの作用はその共役作用です。デフォルトの切り捨ては `max_weight`、`max_freq`、および `max_sins` です。カスタム切り捨て関数は、シグネチャ `customtruncfunc(pstr::PauliStringType, coefficient)::Bool` で渡すことができます。さらに、`kwargs` は下位レベルの関数 `applymergetruncate!`、`applytoall!`、`applyandadd!`、および `apply` に渡されます。
