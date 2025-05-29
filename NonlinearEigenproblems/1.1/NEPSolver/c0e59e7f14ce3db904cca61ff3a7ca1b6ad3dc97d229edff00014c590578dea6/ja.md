```
jd_betcke([eltype]], nep::ProjectableNEP; [neigs=1], [tol=eps(real(T))*100], [maxit=100], [λ=zero(T)], [orthmethod=DGKS],  [errmeasure], [linsolvercreator=DefaultLinSolverCreator()], [v = randn(size(nep,1))], [logger=0], [inner_logger=0], [inner_solver_method=DefaultInnerSolver()], [projtype=:PetrovGalerkin], [target=zero(T)])
```

この関数は、投影法であるJacobi-Davidson法を使用して固有値を計算します。投影された問題は、`inner_solver_method`タイプを通じて指定されたソルバーを使用して解決されます。内部ソルバーのログは、`logger`と同様に機能する`inner_logger`によって決定されます。数値的安定性のために基底は直交のまま保持され、直交化の方法は`orthmethod`によって指定されます。パッケージ`IterativeSolvers.jl`を参照してください。この関数は`neigs`個の固有値を計算しようとし、計算できない場合は`NoConvergenceException`をスローします。値`λ`とベクトル`v`は固有対の初期推測です。`linsolvercreator`は、線形システムがどのように作成され、解決されるかを指定する関数です。`target`は固有値が計算される中心です。デフォルトでは、このメソッドはPetrov-Galerkinフレームワークを使用し、試行（左）空間とテスト（右）空間を持ち、したがって$W^H T(λ) V$が考慮される投影です。`projtype`を`:Galerkin`に指定すると、`W=V`になります。

他のパラメータについては[`augnewton`](@ref)を参照してください。

# 例

```julia-repl
julia> nep=nep_gallery("dep0",50);
julia> λ,v=jd_betcke(nep,tol=1e-8,maxit=20);
julia> norm(compute_Mlincomb(nep,λ[1],v[:,1]))
1.9570222439914163e-10
```

# 参考文献

  * T. Betcke and H. Voss, A Jacobi-Davidson-type projection method for nonlinear eigenvalue problems. Future Gener. Comput. Syst. 20, 3 (2004), pp. 363-372.
  * H. Voss, A Jacobi–Davidson method for nonlinear eigenproblems. In: International Conference on Computational Science. Springer, Berlin, Heidelberg, 2004. pp. 34-41.

参照してください

  * C. Effenberger, Robust successive computation of eigenpairs for nonlinear eigenvalue problems. SIAM J. Matrix Anal. Appl. 34, 3 (2013), pp. 1231-1256.
