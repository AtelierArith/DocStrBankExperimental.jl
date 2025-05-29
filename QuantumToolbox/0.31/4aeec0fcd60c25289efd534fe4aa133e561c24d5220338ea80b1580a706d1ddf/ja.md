```
eigsolve_al(
    H::Union{AbstractQuantumObject{HOpType},Tuple},
    T::Real,
    c_ops::Union{Nothing,AbstractVector,Tuple} = nothing;
    alg::OrdinaryDiffEqAlgorithm = Tsit5(),
    params::NamedTuple = NamedTuple(),
    ρ0::AbstractMatrix = rand_dm(prod(H.dimensions)).data,
    eigvals::Int = 1,
    krylovdim::Int = min(10, size(H, 1)),
    maxiter::Int = 200,
    eigstol::Real = 1e-6,
    kwargs...,
)
```

アルノルディ・リンドブラッド法を使用してリウビリアン超演算子 `L` の固有値問題を解きます。

# 引数

  * `H`: 系のハミルトニアン（または直接リウビリアン）。[`QuantumObject`](@ref)、[`QuantumObjectEvolution`](@ref)、または[`mesolve`](@ref)でサポートされている形式のタプルであることができます。
  * `T`: 時間発展を評価する時間。
  * `c_ops`: 崩壊演算子のベクトル。デフォルトは `nothing` で、システムが閉じていることを意味します。
  * `alg`: 常微分方程式ソルバーアルゴリズム。デフォルトは `Tsit5()` です。
  * `params`: 系のパラメータを含む `NamedTuple`。
  * `ρ0`: 初期密度行列。指定されていない場合は、ランダムな密度行列が使用されます。
  * `eigvals`: 計算する固有値の数。
  * `krylovdim`: クライロフ部分空間の次元。
  * `maxiter`: 固有値ソルバーの最大反復回数。
  * `eigstol`: 固有値ソルバーの許容誤差。
  * `kwargs`: 常微分方程式ソルバーに渡される追加のキーワード引数。

# 注意事項

  * `alg` に関する詳細は、[`DifferentialEquations.jl` (ODE Solvers)](https://docs.sciml.ai/DiffEqDocs/stable/solvers/ode_solve/)を参照してください。
  * `kwargs` に関する詳細は、[`DifferentialEquations.jl` (Keyword Arguments)](https://docs.sciml.ai/DiffEqDocs/stable/basics/common_solver_opts/)を参照してください。

# 戻り値

  * `EigsolveResult`: 固有値、固有ベクトル、および固有値ソルバーに関する情報を含む構造体

# 参考文献

  * [1] Minganti, F., & Huybrechts, D. (2022). Arnoldi-Lindblad time evolution: Faster-than-the-clock algorithm for the spectrum of time-independent and Floquet open quantum systems. Quantum, 6, 649.
