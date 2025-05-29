```
P = dss2pm(sys; fast = true, atol = 0, atol1 = atol, atol2 = atol, gaintol = 0, rtol = min(atol1,atol2) > 0 ? 0 : n*ϵ, val)
```

記述システム `sys = (A-λE,B,C,D)` のために、システム `sys` の伝達関数行列を表す多項式行列 `P(λ) = C*inv(λE-A)*B+D` を構築します。

キーワード引数 `atol1` と `atol2` は、それぞれ `A`、`B`、`C`、`D` の要素と `E` の要素の絶対許容誤差を指定し、`rtol` は `A`、`B`、`C`、`D` および `E` の非ゼロ要素の相対許容誤差を指定します。デフォルトの相対許容誤差は `n*ϵ` であり、ここで `n` は状態、入力、および出力ベクトルの最大次元、`ϵ` は作業用マシンエプシロンです。キーワード引数 `atol` は、同時に `atol1 = atol`、`atol2 = atol` および `gaintol = atol` を設定するために使用できます。

キーワード引数 `gaintol` は、ゲイン行列 `C*inv(γE-A)*B+D` の非ゼロ要素の大きさの閾値を指定します。ここで、`γ = val` は `val` が数値の場合、または `val = missing` の場合は `γ` が単位の大きさを持つランダムに選ばれた複素数値です。一般に、`val` は `P` のいずれかのエントリのゼロであってはなりません。

*方法:* `P(λ)` の各エントリは、その有限ゼロとゲインに対応する多項式から、[1] の方法を使用して構築されます。

*参考文献:*

[1] A. Varga Computation of transfer function matrices of generalized state-space models.      Int. J. Control, 50:2543–2561, 1989.
