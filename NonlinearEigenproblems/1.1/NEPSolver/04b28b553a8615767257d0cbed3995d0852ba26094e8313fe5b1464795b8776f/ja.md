```
ilan(nep,[maxit=30,][σ=0,][γ=1,][linsolvecreator=DefaultLinSolverCreator(),][tolerance=eps()*10000,][neigs=6,][errmeasure,][v=rand(size(nep,1),1),][logger=0,][check_error_every=30,][orthmethod=DGKS])
```

`nep`に格納された対称非線形固有値問題に対して無限ランチョス法を実行します。現在の実装は、`SPMF`形式の`nep`のみをサポートしています。

ターゲット`σ`は、固有値が計算される中心です。キーワード引数`errmeasure`は、終了時に使用されるエラーの測定方法を指定するために使用できる関数ハンドルです（デフォルトは絶対残差ノルム）。リッツペア`λ`と`v`は、`errmeasure`が`tol`未満である場合に収束した（固有ペアに）とフラグ付けされます。ベクトル`v`は、クリロフ空間を構築するための開始ベクトルです。クリロフ空間の直交基底を構築する際に使用される直交化方法は`orthmethod`によって指定されます。詳細は`IterativeSolvers.jl`パッケージを参照してください。反復は、`neigs`リッツペアが収束するまで続けられます。この関数は、`maxit`回の反復後に希望する固有ペアが計算されない場合、`NoConvergenceException`をスローします。ただし、`neigs`が`Inf`に設定されている場合、エラーがスローされることなく`maxit`回の反復が続けられます。

他のパラメータについては[`augnewton`](@ref)を参照してください。

# 例

```julia-repl
julia> using NonlinearEigenproblems, LinearAlgebra
julia> nep=nep_gallery("dep_symm_double",10);
julia> v0=ones(size(nep,1));
julia> λ,v=ilan(nep;v=v0,tol=1e-5,neigs=3);
julia> norm(compute_Mlincomb!(nep,λ[1],v[:,1])) # これは固有値ですか？
julia> λ    # 計算された固有値を表示
3-element Array{Complex{Float64},1}:
  0.03409997385842267 - 1.425205509434608e-19im
 -0.03100798730589012 + 5.66201058098364e-20im
  -0.0367653644764646 - 1.607494907684445e-19im
```

# 参考文献

  * Meleによるアルゴリズム2、対称非線形固有値問題のための無限ランチョス法、https://arxiv.org/abs/1812.07557、2018
