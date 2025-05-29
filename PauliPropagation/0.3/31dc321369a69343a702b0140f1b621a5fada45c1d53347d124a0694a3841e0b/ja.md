```
propagate(circ, psum::PauliSum, thetas=nothing; max_weight=Inf, min_abs_coeff=1e-10, max_freq=Inf, max_sins=Inf, customtruncfunc=nothing, kwargs...)
```

回路 `circ` を通して `PauliSum` をハイゼンベルク表現で伝播させます。これは、回路が逆順でパウリ和に適用され、各ゲートの作用がその共役作用であることを意味します。`circ` のパラメータ化されたゲートのパラメータは `thetas` によって与えられ、シュレーディンガー表現で記述されたように回路が適用されたかのように渡す必要があります。`thetas` が渡されない場合、回路は非パラメータ化された `StaticGates` のみを含む必要があります。デフォルトの切り捨ては `max_weight`、`min_abs_coeff`、`max_freq`、および `max_sins` です。`max_freq` と `max_sins` は `PauliFreqTracker` の係数とのみ使用できます。カスタム切り捨て関数は、シグネチャ `customtruncfunc(pstr::PauliStringType, coefficient)::Bool` で `customtruncfunc` として渡すことができます。さらに、`kwargs` は下位レベルの関数 `applymergetruncate!`、`applytoall!`、`applyandadd!`、および `apply` に渡されます。
