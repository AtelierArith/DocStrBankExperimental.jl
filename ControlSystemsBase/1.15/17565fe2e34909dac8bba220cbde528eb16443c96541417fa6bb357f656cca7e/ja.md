```
Ninf, ω_peak = linfnorm(sys; tol=1e-6)
```

LTIシステム`sys`のL∞ノルム`Ninf`を計算し、ゲイン`Ninf`が達成される周波数`ω_peak`を求めます。

`Ninf := sup_ω σ_max[sys(iω)]`（σ_maxは最大特異値を示します）

`tol`は、計算されたL∞ノルムの相対精度を表すオプションのキーワード引数です（これは絶対的な証明ではありません）。

`sys`は必要に応じて状態空間モデルに変換されます。

連続時間L∞ノルム計算は、以下の文献における「二段階アルゴリズム」を実装しています： **N.A. Bruinsma and M. Steinbuch**, 'A fast algorithm to compute the H∞-norm of a transfer function matrix', Systems and Control Letters (1990), pp. 287-293.

離散時間バージョンについては、以下を参照してください： **P. Bongers, O. Bosgra, M. Steinbuch**, 'L∞-norm calculation for generalized state space systems in continuous and discrete time', American Control Conference, 1991.

また、[`hinfnorm`](@ref)も参照してください。
