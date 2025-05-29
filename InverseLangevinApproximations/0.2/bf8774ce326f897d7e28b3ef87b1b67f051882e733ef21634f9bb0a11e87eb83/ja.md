```julia
inverse_langevin_approximation(
    y,
    m::InverseLangevinApproximations.AbstractInverseLangevinApproximation
) -> Any

```

逆ランジュバン関数を計算するためのメソッド。

  * `y`: ランジュバン関数の値
  * `m`: 近似メソッド
