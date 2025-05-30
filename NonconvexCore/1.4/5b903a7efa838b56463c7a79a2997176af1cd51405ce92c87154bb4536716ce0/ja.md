```
許容誤差
```

アルゴリズムの収束を評価するために使用される異なる許容誤差を指定する構造体です。`Tolerance`のフィールドは以下の通りです：

  * `x`: [`ConvergenceState`](@ref)における`Δx`の許容誤差。`Δx`が`Tolerance`の`x`許容誤差より小さい場合、`x_converged`はtrueになります。これは、[`GenericCriteria`](@ref)が収束基準として使用される場合に収束を評価するために使用されます。
  * `fabs`: [`ConvergenceState`](@ref)における`Δf`の許容誤差。`Δf`が`Tolerance`の`fabs`許容誤差より小さい場合、`f_converged`はtrueになります。これは、[`GenericCriteria`](@ref)が収束基準として使用される場合に収束を評価するために使用されます。
  * `frel`: [`ConvergenceState`](@ref)における`relΔf`の許容誤差。`relΔf`が`Tolerance`の`frel`許容誤差より小さい場合、`f_converged`はtrueになります。これは、[`GenericCriteria`](@ref)が収束基準として使用される場合に収束を評価するために使用されます。
  * `kkt`: KKT許容誤差。[`ConvergenceState`](@ref)の`kkt_converged`は、`kkt_residual`がKKT許容誤差より小さい場合にtrueになります。また、[`ConvergenceState`](@ref)の`ipopt_converged`は、`ipopt_residual`がKKT許容誤差より小さい場合にtrueになります。これは、[`KKTCriteria`](@ref)、[`ScaledKKTCriteria`](@ref)または[`IpoptCriteria`](@ref)基準が収束基準として使用される場合に収束を評価するために使用されます。
  * `infeas`: 最大不適合許容誤差。[`ConvergenceState`](@ref)の`infeas_converged`は、最大不適合が不適合許容誤差より小さい場合にtrueになります。これは、使用される収束基準に関係なく収束を評価するために使用されます。

収束基準についての詳細は、[`GenericCriteria`](@ref)、[`KKTCriteria`](@ref)、[`ScaledKKTCriteria`](@ref)および[`IpoptCriteria`](@ref)を参照してください。
