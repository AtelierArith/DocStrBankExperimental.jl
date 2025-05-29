```
uzal_cost_local(Y::Dataset; kwargs...) → L_local
```

入力データセット `Y` に対して Uzal et al.[^Uzal2011] に従ってローカル L-統計量 `L_local` を計算します。`L_local` の長さは `length(Y)-Tw` であり、状態空間軌道の各点に対するローカルコスト関数の値を示します。

[`uzal_cost`](@ref) と対照的に、ここでは `σ²` がアトラクタ上のすべての状態空間参照点で平均化されません。したがって、`uzal*cost` を呼び出す際に 'L*local' の平均は `L` と異なります。なぜなら、平均化は対数化の前に行われるからです。

キーワードは [`uzal_cost`](@ref) と同様です。

[^Uzal2011]: Uzal, L. C., Grinblat, G. L., Verdes, P. F. (2011). [Optimal reconstruction of dynamical systems: A noise amplification approach. Physical Review E 84, 016223](https://doi.org/10.1103/PhysRevE.84.016223).
