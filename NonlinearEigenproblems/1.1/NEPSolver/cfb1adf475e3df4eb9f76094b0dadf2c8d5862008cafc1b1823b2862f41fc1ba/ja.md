```
iar_chebyshev(nep,[maxit=30,][σ=0,][γ=1,][linsolvecreator=DefaultLinSolverCreator(),][tolerance=eps()*10000,][neigs=6,][errmeasure,][v=rand(size(nep,1),1),][logger=0,][check_error_every=1,][orthmethod=DGKS][a=-1,][b=1,][compute_y0_method=ComputeY0ChebAuto])
```

非線形固有値問題 `nep` に対して無限アーノルディ法（チェビシェフ版）を実行します。

ターゲット `σ` は固有値が計算される中心です。リッツペア `λ` と `v` は、`errmeasure` が `tol` より小さい場合に収束した（固有ペアに）とフラグ付けされます。ベクトル `v` はクリロフ空間を構築するための開始ベクトルです。クリロフ空間の直交基底を構築する際に使用される直交化方法は `orthmethod` によって指定されます。詳細はパッケージ `IterativeSolvers.jl` を参照してください。`neigs` リッツペアが収束するまで反復が続けられます。この関数は、`maxit` 回の反復後に希望する固有ペアが計算されない場合、`NoConvergenceException` をスローします。ただし、`neigs` が `Inf` に設定されている場合、エラーがスローされることなく `maxit` 回の反復が続けられます。キーワード引数 `compute_y0_method` は、次のクリロフ空間のベクトル（チェビシェフ形式）をどのように計算できるかを指定します。詳細は、コマンド `?NEPSolver.compute_y0_cheb` でモジュール NEPSolver の [`compute_y0_cheb`](@ref) を参照してください。

他のパラメータについては [`augnewton`](@ref) を参照してください。

# 例

```julia-repl
julia> using NonlinearEigenproblems, LinearAlgebra
julia> nep=nep_gallery("dep0",100);
julia> v0=ones(size(nep,1));
julia> λ,v=iar_chebyshev(nep;v=v0,tol=1e-5,neigs=3);
julia> norm(compute_Mlincomb!(nep,λ[1],v[:,1])) # これは固有値ですか？
julia> λ    # 計算された固有値を表示
3-element Array{Complex{Float64},1}:
julia> norm(compute_Mlincomb(nep,λ[1],v[:,1]))
 0.050462487848960284 - 1.4289626573515395e-18im
 -0.07708779190301127 + 7.703053374113074e-18im
   0.1503856540695659 - 1.662582577182149e-17im
```

# 参考文献

  * Jarlebring, Michiels Meerbergen におけるアルゴリズム 2、非線形固有値問題のための線形固有値アルゴリズム、Numer. Math, 2012
