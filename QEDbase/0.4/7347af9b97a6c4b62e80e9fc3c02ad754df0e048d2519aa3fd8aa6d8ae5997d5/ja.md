```julia
isonshell(mom, mass)

```

与えられた質量 `mass` に対する与えられた四元運動量 `mom` のオンシェルチェック。

!!! note "精度"
    `AbstactFourMomentum` の場合、要素型は `Float64` に固定されており、要素間の比較の精度が制限されています。現在の実装は、エネルギースケール `E` の範囲 `1e-9 <= E <= 1e5` 内でテストされています。その範囲内では、オフシェルとして正しく検出される質量誤差は、成分の平均値の `1e-4` 倍ですが、最大値は `0.01` です。例えば、高エネルギー端ではそうなります。エネルギースケールは、下限で `0.5 meV`、上限で `50 GeV` に対応します。


!!! todo "実数エントリを持つ四元運動量"
      * `AbstractFourMomentum` が要素型 `T<:Real` に更新される場合、`AbstractLorentzVector` も `AbstractFourMomentum` で更新されるべきです。

