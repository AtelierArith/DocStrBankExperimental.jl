```julia
mutable struct KrylovLS{K, Tl, Tr} <: BifurcationKit.AbstractIterativeLinearSolver
```

[Krylov.jl](https://jso.dev/Krylov.jl)に基づいた線形ソルバーを作成します。これは、`(a₀ * I + a₁ * J) * x = rhs`を解くために使用できます。`cg, cr, gmres, symmlq, cg_lanczos, cg_lanczos_shift_seq`にアクセスできます...

## フィールド

  * `KrylovAlg::Symbol`: Krylovメソッド
  * `kwargs::Any`: 線形ソルバーに渡される引数
  * `Pl::Any`: 左前処理器
  * `Pr::Any`: 右前処理器

## その他のメソッド

Krylov空間がメモリに保持されるメソッドについては`KrylovLSInplace`を参照してください。
