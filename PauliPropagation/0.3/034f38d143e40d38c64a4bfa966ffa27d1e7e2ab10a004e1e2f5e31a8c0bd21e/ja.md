```
estimatemse!(circ, pstr::PauliString, error_array::AbstractVector, thetas, split_probabilities; stateoverlapfunc=overlapwithzero, circuit_is_reversed=false, kwargs...)
```

`estimatemse`のインプレースバージョン。この関数は、引数として長さ`n_mcsamples`の配列`error_array`を取り、それをインプレースで修正します。さらに、`thetas`と`split_probabilities`がすでに正しく計算され、引数として提供されていると仮定します。一般的にはベクトルですが、実数であることもあります。カスタム切り捨て関数は、シグネチャ`customtruncfunc(pstr::PauliStringType, coefficient)::Bool`を持つ`customtruncfunc`として渡すことができます。
