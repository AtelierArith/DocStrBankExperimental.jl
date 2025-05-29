```
Ninf, ω_peak = hinfnorm(sys; tol=1e-6)
```

LTIシステム`sys`のH∞ノルム`Ninf`を計算し、Ninfが達成される周波数`ω_peak`を求めます。

`Ninf := sup_ω σ_max[sys(iω)]`  もし`G`が安定であれば（σ_max = 最大特異値）       :=        `Inf'           もし`G`が不安定であれば

`tol`は計算されたH∞ノルムのための望ましい相対精度のオプションのキーワード引数です（絶対的な証明ではありません）。

`sys`は必要に応じて状態空間モデルに変換されます。

連続時間L∞ノルム計算は、以下の「二段階アルゴリズム」を実装しています： **N.A. Bruinsma and M. Steinbuch**, 'A fast algorithm to compute the H∞-norm of a transfer function matrix', Systems and Control Letters (1990), pp. 287-293.

離散時間バージョンについては、次を参照してください： **P. Bongers, O. Bosgra, M. Steinbuch**, 'L∞-norm calculation for generalized state space systems in continuous and discrete time', American Control Conference, 1991.

また、[`linfnorm`](@ref)も参照してください。
