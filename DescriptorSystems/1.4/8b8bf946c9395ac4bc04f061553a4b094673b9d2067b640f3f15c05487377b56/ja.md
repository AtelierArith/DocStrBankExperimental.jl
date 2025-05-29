```
R = dss2rm(sys; fast = true, atol = 0, atol1 = atol, atol2 = atol, gaintol = atol, rtol = min(atol1,atol2) > 0 ? 0 : n*ϵ, val)
```

記述システム `sys = (A-λE,B,C,D)` のために、システム `sys` の伝達関数行列を表す有理行列 `R(λ) = C*inv(λE-A)*B+D` を構築します。

キーワード引数 `atol1` と `atol2` は、それぞれ `A`、`B`、`C`、`D` の要素と `E` の要素の絶対許容誤差を指定し、`rtol` は `A`、`B`、`C`、`D` および `E` の非ゼロ要素の相対許容誤差を指定します。デフォルトの相対許容誤差は `n*ϵ` であり、ここで `n` は状態、入力、および出力ベクトルの最大次元、`ϵ` は作業用マシンイプシロンです。キーワード引数 `atol` は、同時に `atol1 = atol`、`atol2 = atol` および `gaintol = atol` を設定するために使用できます。

キーワード引数 `gaintol` は、ゲイン行列 `C*inv(γE-A)*B+D` の非ゼロ要素の大きさの閾値を指定します。ここで、`γ = val` は `val` が数値の場合、または `val = missing` の場合は `γ` が単位大きさのランダムに選ばれた複素数値です。一般に、`val` は `R` のいずれかのエントリのゼロであってはなりません。

*メソッド:* `R(λ)` の各有理エントリは、その有限ゼロ、有限極およびゲインに対応する分子および分母多項式から構築されます。[1] の方法を使用します。

*参考文献:*

[1] A. Varga Computation of transfer function matrices of generalized state-space models.      Int. J. Control, 50:2543–2561, 1989.
