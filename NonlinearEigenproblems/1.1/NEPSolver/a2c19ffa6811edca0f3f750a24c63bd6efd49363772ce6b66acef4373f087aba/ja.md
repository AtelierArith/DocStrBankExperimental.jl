```
jd_effenberger([eltype]], nep::ProjectableNEP; [maxit=100], [neigs=1], [inner_solver_method=DefaultInnerSolver()], [orthmethod=DGKS()], [linsolvercreator=DefaultLinSolverCreator()], [tol=eps(real(T))*100], [λ=zero(T)], [v = rand(T,size(nep,1))], [target=zero(T)],  [logger=0], [inner_logger=0])
```

この関数は、投影法であるJacobi-Davidson法を使用して固有値を計算します。繰り返し固有値は、Effenbergerによる参考文献に示されているように、除外を使用することで回避されます。投影された問題は、`inner_solver_method`という型を通じて指定されたソルバーを使用して解決されます。内部ソルバーのログは`inner_logger`によって決定され、これは`logger`と同じように機能します。数値的安定性のために基底は直交のまま保持され、直交化の方法は`orthmethod`によって指定されます。詳細は`IterativeSolvers.jl`パッケージを参照してください。この関数は`neigs`個の固有値を計算しようとし、計算できない場合は`NoConvergenceException`をスローします。値`λ`とベクトル`v`は固有対の初期推定値です。`linsolvercreator`は線形システムがどのように作成され、解決されるかを指定する関数です。`target`は固有値が計算される中心です。`deflation_mode`に関するさらなる仕様については、関数`deflate_eigpair`を参照してください。

他のパラメータについては[`augnewton`](@ref)を参照してください。

# 例

```julia-repl
julia> nep=nep_gallery("dep0",100);
julia> λ,v=jd_effenberger(nep,maxit=30,v=ones(size(nep,1)),λ=0);
julia> norm(compute_Mlincomb(nep,λ[1],v[:,1]))
9.577305772525487e-15
```

# 参考文献

  * C. Effenberger, 非線形固有値問題のための堅牢な連続固有対計算. SIAM J. Matrix Anal. Appl. 34, 3 (2013), pp. 1231-1256.

さらに参照

  * T. Betcke and H. Voss, 非線形固有値問題のためのJacobi-Davidson型投影法. Future Gener. Comput. Syst. 20, 3 (2004), pp. 363-372.
  * H. Voss, 非線形固有問題のためのJacobi–Davidson法. 国際計算科学会議において. Springer, Berlin, Heidelberg, 2004. pp. 34-41.
