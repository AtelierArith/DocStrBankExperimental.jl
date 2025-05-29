```julia
mutable struct KrylovLSInplace{F, K, Tl, Tr} <: BifurcationKit.AbstractIterativeLinearSolver
```

[Krylov.jl](https://jso.dev/Krylov.jl)に基づいてインプレース線形ソルバーを作成します。これは、`(a₀ * I + a₁ * J) * x = rhs`を解くために使用できます。

クライロフ空間は事前に割り当てられています。これはGPUにとって非常に素晴らしいですが、CPUにとっても同様です。

## フィールド

  * `workspace::Any`: 例えばKrylov.GmresWorkspaceである可能性があります
  * `KrylovAlg::Symbol`: クライロフ法
  * `kwargs::Any`: 線形ソルバーに渡される引数
  * `Pl::Any`: 左前処理器
  * `Pr::Any`: 右前処理器
  * `is_inplace::Bool`: 線形マッピングはインプレースかどうか
