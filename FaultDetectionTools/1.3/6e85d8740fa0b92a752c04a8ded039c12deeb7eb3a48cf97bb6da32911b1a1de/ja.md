```
 fdiscond_(sysrf::DescriptorStateSpace, freq) -> (scond, β, γ)
```

安定した記述子システム `sysrf = (A-λE,B,C,D)` に対して、伝達関数行列 `Rf(λ)` を用いて、`β` - `Rf(λ)` の H∞- 指数、`γ` - `Rf(λ)` の列ノルムの最大値、`scond` - `scond := β/γ` として評価される列ゲイン感度条件を計算します。もし `freq` が実周波数値のベクトルであれば、`β` と `γ` は `freq` に含まれる周波数に対して評価されます。
