```
struct SchrodingerProblem
SchrodingerProblem(reg, tspan, hamiltonian; kw...)
```

シュレーディンガー方程式の問題を定義し、`OrdinaryDiffEq`のODEソルバーを使用して動力学を解決します。

# 引数

  * `register`: 必須、進化問題のレジスタ、[`SubspaceArrayReg`](@ref)または`Yao`の`ArrayReg`である必要があります。
  * `tspan`: 必須、`(start, stop)`タプルまたは単一の数値`t`、単一の値形式`t`は`(zero(t), t)`と同等です。
  * `hamiltonian`: 必須、進化ハミルトニアン、[`rydberg_h`](@ref)を介して作成できます。

# 一般的なキーワード引数

  * `algo`: オプション、使用するアルゴリズム、これは`emulate!`インターフェースにのみ機能します。`solve`または積分器インターフェースの場合、アルゴリズムを明示的に指定する必要があります。
  * `progress`: 進捗バーを表示するかどうか、問題のスケールが小さい場合、パフォーマンスに影響を与える可能性があります。デフォルトは`true`です。
  * `progress_steps`: 進捗バーを更新するステップ、デフォルトは`5`です。
  * `reltol`: 相対許容誤差、デフォルトは1e-8です。
  * `abstol`: 絶対許容誤差、デフォルトは1e-8です。

# さらなる参考

より多くのODEオプションについては、[Common Solver Options](https://diffeq.sciml.ai/stable/basics/common_solver_opts/)を参照してください。`SchrodingerProblem`型は、標準のDiffEq問題インターフェースのほとんどをサポートしています。
