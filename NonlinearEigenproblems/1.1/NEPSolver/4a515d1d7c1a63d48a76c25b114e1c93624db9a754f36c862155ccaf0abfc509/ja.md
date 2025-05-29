```
iar(nep,[maxit=30,][σ=0,][γ=1,][linsolvecreator=DefaultLinSolverCreator(),][tol=eps()*10000,][neigs=6,][errmeasure,][v=rand(size(nep,1),1),][logger=0,][check_error_every=1,][orthmethod=DGKS,][proj_solve=false,][inner_solver_method=DefaultInnerSolver(),][inner_logger=0])
```

非線形固有値問題に対して無限アーノルディ法を実行します。`nep`に格納された問題です。

ターゲット`σ`は、固有値が計算される中心です。値`γ`はスケーリングに対応し、シフトとスケーリングを指定することは、実際には変換`λ=γs+σ`と同じです。ここで`s`は固有値パラメータです。中心が`σ`で半径が`γ`の円盤内の固有値を取得したい場合は、`σ`を円盤の中心として選択します。ベクトル`v`は、クリロフ空間を構築するための開始ベクトルです。クリロフ空間の直交基底を構築する際に使用される直交化方法は`orthmethod`によって指定されます。詳細はパッケージ`IterativeSolvers.jl`を参照してください。反復は、`neigs`リッツペアが収束するまで続けられます。この関数は、`maxit`回の反復後に希望する固有ペアが計算されない場合、`NoConvergenceException`をスローします。ただし、`neigs`が`Inf`に設定されている場合、エラーがスローされることなく`maxit`回の反復が続けられます。パラメータ`proj_solve`は、リッツペアがヘッセンベルグ行列を使用して抽出されるか（false）、または投影問題の解として抽出されるか（true）を決定します。`true`の場合、メソッドは`inner_solver_method`によって決定され、内部ソルバーのログは`inner_logger`によって決定されます。これは`logger`と同じように機能します。

他のパラメータについては[`augnewton`](@ref)を参照してください。

# 例

```julia-repl
julia> using NonlinearEigenproblems, LinearAlgebra
julia> nep=nep_gallery("dep0",100);
julia> v0=ones(size(nep,1));
julia> λ,v=iar(nep;v=v0,tol=1e-5,neigs=3);
julia> norm(compute_Mlincomb!(nep,λ[1],v[:,1])) # これは固有値ですか？
julia> λ    # 計算された固有値を表示
3-element Array{Complex{Float64},1}:
 -0.15606211475666945 - 0.12273439802763578im
 -0.15606211475666862 + 0.12273439802763489im
  0.23169243065648365 - 9.464790582509696e-17im
```

# 参考文献

  * Jarlebring, Michiels Meerbergenによるアルゴリズム2、非線形固有値問題のための線形固有値アルゴリズム、Numer. Math, 2012
