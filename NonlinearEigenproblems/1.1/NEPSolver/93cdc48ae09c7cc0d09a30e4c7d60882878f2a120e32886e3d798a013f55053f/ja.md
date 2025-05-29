```
tiar(nep,[maxit=30,][σ=0,][γ=1,][linsolvecreator=DefaultLinSolverCreator(),][tolerance=eps()*10000,][neigs=6,][errmeasure,][v=rand(size(nep,1),1),][logger=0,][check_error_every=1,][orthmethod=DGKS(),][proj_solve=false,][inner_solver_method=DefaultInnerSolver(),][inner_logger=0])
```

非線形固有値問題に対してテンソル無限アーノルディ法を実行します。これは `iar` と同等ですが、テンソル表現を用いて直交化を処理します。

ターゲット `σ` は固有値が計算される中心です。値 `γ` はスケーリングに対応し、シフトとスケーリングを指定することは、実際には変換 `λ=γs+σ` と同じです。ここで `s` は固有値パラメータです。中心に固有値がある円盤内の固有値を取得したい場合は、`σ` を円盤の中心として、`γ` を半径として選択します。ベクトル `v` はクリロフ空間を構築するための開始ベクトルです。クリロフ空間の直交基底を構築する際に使用される直交化方法は `orthmethod` によって指定されます。詳細はパッケージ `IterativeSolvers.jl` を参照してください。反復は `neigs` リッツ対が収束するまで続けられます。この関数は、`maxit` 回の反復後に希望する固有対が計算されない場合、`NoConvergenceException` をスローします。ただし、`neigs` が `Inf` に設定されている場合、エラーがスローされることなく `maxit` 回の反復が続けられます。パラメータ `proj_solve` は、リッツ対がヘッセンベルグ行列を使用して抽出されるか（false）、または投影問題の解として抽出されるか（true）を決定します。true の場合、メソッドは `inner_solver_method` によって決定され、内部ソルバーのログは `inner_logger` によって決定されます。これは `logger` と同じように機能します。

他のパラメータについては [`augnewton`](@ref) を参照してください。

# 例

```julia-repl
julia> using NonlinearEigenproblems, LinearAlgebra
julia> nep=nep_gallery("dep0",100);
julia> v0=ones(size(nep,1));
julia> λ,v=tiar(nep;v=v0,tol=1e-5,neigs=3);
julia> norm(compute_Mlincomb!(nep,λ[1],v[:,1])) # これは固有値ですか？
julia> λ    # 計算された固有値を表示
3-element Array{Complex{Float64},1}:
 0.050462487743188206 - 3.4059600538119376e-18im
 -0.07708769561361105 + 8.611006691570004e-19im
   0.1503916927814904 + 9.388210527944734e-18im
```

# 参考文献

  * Jarlebring, Mele, Runborg のアルゴリズム 2, The Waveguide Eigenvalue Problem and the Tensor Infinite Arnoldi Method, SIAM J. Scient. computing, 39 (3), A1062-A1088, 2017
