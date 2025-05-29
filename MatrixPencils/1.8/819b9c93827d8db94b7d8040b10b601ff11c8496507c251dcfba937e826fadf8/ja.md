```
lps2rm(A, E, B, F, C, G, D, H; fast = true, atol1 = 0, atol2 = 0, gaintol = 0, rtol = min(atol1,atol2) > 0 ? 0 : n*ϵ, val) -> (NUM, DEN)
```

構造化線形化に対応する有理行列 `R(λ) = (C-λG)*inv(λE-A)*(B-λF)+D-λH := NUM(λ) ./ DEN(λ)` を構築します。

```
        | A-λE | B-λF | 
 S(λ) = |------|------|
        | C-λG | D-λH |
```

`R(λ)` の各有理成分について、その有限ゼロとゲインから分子係数を明示的に決定し、有限極から分母係数を決定します。[1] のアプローチの拡張が採用され、[2] の手続きを利用して強い不可約線形化を計算します。

キーワード引数 `atol1` と `atol2` は、それぞれ `A`、`B`、`C`、`D` の要素と `E`、`F`、`G`、`H` の要素の絶対許容誤差を指定し、`rtol` は `A`、`B`、`C`、`D`、`E`、`F`、`G`、`H` の非ゼロ要素の相対許容誤差を指定します。デフォルトの相対許容誤差は `(n+2)*ϵ` であり、ここで `n` は `A` のサイズ次元のサイズで、`ϵ` は `A` の係数の要素型の機械イプシロンです。

キーワード引数 `gaintol` は、ゲイン行列 `C*inv(γE-A)*B+D` の非ゼロ要素の大きさの閾値を指定します。ここで `γ = val` は `val` が数値の場合、または `val = missing` の場合は `γ` が単位の大きさのランダムに選ばれた複素数値です。一般に、`val` は `P` のいずれかの成分の根であってはなりません。

[1] A. Varga Computation of transfer function matrices of generalized state-space models.      Int. J. Control, 50:2543–2561, 1989.

[2] F.M. Dopico, M.C. Quintana and P. Van Dooren, Linear system matrices of rational transfer functions,  in "Realization and Model Reduction of Dynamical Systems, A Festschrift to honor the 70th birthday of Thanos Antoulas",  Eds. C. Beattie, P. Benner, M. Embree, S. Gugercin and S. Lefteriu, Springer-Verlag, 2020.  [arXiv:1903.05016](https://arxiv.org/pdf/1903.05016.pdf) ```
