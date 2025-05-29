```
クラッシュ
```

構造化アルゴリズムにおける初期決定を生成するために使用されるクラッシュメソッドのコレクション。

...

# 利用可能なクラッシュメソッド

  * [`None`](@ref)
  * [`EVP`](@ref)
  * [`Scenario`](@ref)
  * [`Custom`](@ref)

...

## 例

以下は、`StochasticPrograms.jl`で作成された確率プログラム`sp`を、信頼領域を持つL字型アルゴリズムと`lpsolver`としてClpを使用し、`EVP`クラッシュで初期決定を生成することで解決します。

```jldoctest
julia> optimize!(sp, solver = LShapedSolver(GLPKSolverLP(), crash=Crash.EVP(), regularize = TrustRegion()))
L-Shaped Gap  Time: 0:00:00 (8 iterations)
  Objective:       -855.8333333333339
  Gap:             0.0
  Number of cuts:  4
  Iterations:      8
:Optimal
```
