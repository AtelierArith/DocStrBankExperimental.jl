```
 monodromy(A::PeriodicTimeSeriesMatrix) -> Ψ::PeriodicArray
```

連続時間の時系列行列に対するモノドロミー行列を計算します。

与えられた周期 `T` の正方形周期行列 `A(t)` とサブ周期 `T′ = T/k`（ここで `k` はサブ周期の数）に対して、モノドロミー行列 `Ψ = Φ(T′,0)` が計算されます。ここで `Φ(t,τ)` は次の均質線形常微分方程式を満たす状態遷移行列です。

```
dΦ(t,τ)/dt = A(t)Φ(t,τ),  Φ(τ,τ) = I.
```

`A` は [`PeriodicTimeSeriesMatrix`](@ref) であり、`K` コンポーネント行列を持ち、結果として得られるモノドロミー行列 `Ψ` は、周期 `T` と `k` サブ周期を持つ離散時間周期配列として格納されます。

`Ψ = Φ(T′,0)` は `K` 行列の積として決定され、`Ψ = Ψ_K*...*Ψ_1` となります。ここで `Δ := T′/K` とし、`Ψ_i = Φ(iΔ,(i-1)Δ)` は時間区間 `[(i-1)Δ,iΔ]` における状態遷移行列です。各状態遷移行列は行列指数関数 `Φ(iΔ,(i-1)Δ) = exp(A[i]*Δ)` として計算され、ここで `A[i]` は時系列表現の `i` 番目のコンポーネント行列です。大きな値の `K` に対しては、Juliaを複数の実行スレッドで起動することにより、因子の並列計算を代替的に行うことができます。実行スレッドの数は、`-t/--threads` コマンドライン引数を使用するか、`JULIA_NUM_THREADS` 環境変数を使用することで制御されます。  
