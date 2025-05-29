```
choiceDDM(θ, n, cross)
```

フィールド:

  * `θ`: `choiceDDM`のすべてのモデルパラメータを含むモジュール定義クラス`θchoice`のインスタンス
  * `n`: 使用する空間ビンの数（デフォルトは53）。
  * `cross`: クロスクリック適応を使用するかどうか（デフォルトはfalse）。
  * `fit`: `choiceDDM`モデルの最適化用の`Bool`の`array`。
  * `lb`: `choiceDDM`モデルの最適化用の下限の`array`。
  * `ub`: `choiceDDM`モデルの最適化用の上限の`array`。

例:

```julia
ntrials, dt, centered, n  = 1, 1e-2, false, 53
θ = θchoice()
_, data = synthetic_data(n ;θ=θ, ntrials=ntrials, rng=1, dt=dt);
choiceDDM(θ=θ, data=data, n=n)
```
