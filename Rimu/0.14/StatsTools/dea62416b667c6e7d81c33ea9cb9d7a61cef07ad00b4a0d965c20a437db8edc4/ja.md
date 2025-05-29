```
variational_energy_estimator(shifts, overlaps; kwargs...)
variational_energy_estimator(df::DataFrame; max_replicas=:all, kwargs...)
variational_energy_estimator(sim::PMCSimulation; kwargs...)
-> r::RatioBlockingResult
```

レプリカの時系列データである `shifts` と係数ベクトル `overlaps` からブロッキング解析によって変分エネルギー推定量を計算します。キーワード引数 `max_replicas` を使用して、`df` にあるすべてのレプリカよりも小さい処理されるレプリカの数を制約することができます。他のキーワード引数は [`ratio_of_means()`](@ref) に渡されます。[`RatioBlockingResult`](@ref) を返します。

変分エネルギーの推定量

$$
\frac{⟨\mathbf{c}⟩^† \mathbf{H}⟨\mathbf{c}⟩}{⟨\mathbf{c}⟩^†⟨\mathbf{c}⟩}
$$

は次のように計算されます。

$$
Ē_{v}  =  \frac{\sum_{a<b}^R \overline{(S_a+S_b) \mathbf{c}_a^† \mathbf{c}_b}}
               {2\sum_{a<b}^R \overline{\mathbf{c}_a^† \mathbf{c}_b}} ,
$$

ここで、合計は $R$ レプリカの異なるペアにわたります。詳細は [arXiv:2103.07800](http://arxiv.org/abs/2103.07800) を参照してください。

`DataFrame` および [`PMCSimulation`](@ref Main.Rimu.PMCSimulation) バージョンは、[`solve`](@ref CommonSolve.solve(::ProjectorMonteCarloProblem)) の結果から関連情報を抽出できます。キーワード引数 `replica_strategy = AllOverlaps(R)` と `R ≥ 2` を使用して [`ProjectorMonteCarloProblem`](@ref Main.ProjectorMonteCarloProblem) を設定します。`shifts` と `overlaps` を渡す場合、データは正しい順序に配置されている必要があります（`DataFrame` バージョンで提供されているように）。

[`AllOverlaps`](@ref Main.AllOverlaps) を参照してください。
