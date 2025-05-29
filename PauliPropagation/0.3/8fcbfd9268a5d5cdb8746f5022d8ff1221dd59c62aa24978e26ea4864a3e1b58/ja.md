```
propagate!(circ, psum::PauliSum, thetas=nothing; max_weight=Inf, min_abs_coeff=1e-10, max_freq=Inf, max_sins=Inf, customtruncfunc=nothing, kwargs...)
```

回路 `circ` を通してパウリ和をヘisenberg 画像で伝播させます。これは、回路がパウリ和に逆順で適用され、各ゲートの作用がその共役作用であることを意味します。入力 `psum` は変更されます。`circ` のパラメータ化されたゲートのパラメータは `thetas` によって与えられ、シュレーディンガー画像で書かれたように回路が適用されたかのように渡す必要があります。`thetas` が渡されない場合、回路は非パラメータ化された `StaticGates` のみを含む必要があります。デフォルトの切り捨ては `max_weight`、`min_abs_coeff`、`max_freq`、および `max_sins` です。`max_freq` と `max_sins` は `PauliFreqTracker` の係数とだけ使用できます。カスタム切り捨て関数は、シグネチャ `customtruncfunc(pstr::PauliStringType, coefficient)::Bool` として `customtruncfunc` として渡すことができます。さらに、`kwargs` は低レベルの関数 `applymergetruncate!`、`applytoall!`、`applyandadd!`、および `apply` に渡されます。
