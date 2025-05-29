```
λ,v = sgiter([eltype],nep::NEP,j::Integer;[λ_min,][λ_max,][λ,][errmeasure,][tol,][maxit,][logger,][eigsolvertype::Type,])
```

NEPの`j`-番目の固有値を保護された反復を使用して見つけます。固有値の番号付けは最小-最大理論に従います。この方法はエルミート問題にのみ適用され、固有値は実数であると仮定されます。区間 [`λ_min`,`λ_max`] が与えられた場合、レイリー関数はその区間で一意であると仮定されます。区間が与えられない場合、常に最小解が取られます。この方法は行列の（すべての）固有値の計算を必要とします。`eigsolvertype` は、アルゴリズム内で使用される固有値ソルバーを指定する `Type` です。

他のパラメータについては [`augnewton`](@ref) を参照してください。

# 例

```julia-repl
julia> nep = nep_gallery("real_quadratic");
julia> λ,v = sgiter(nep, 1, λ_min = -10, λ_max = 0,  λ = -10, maxit = 100);
julia> minimum(svdvals(compute_Mder(nep,λ)))
0.0
julia> norm(v)
1.0
```

# 参考文献

  * V. Mehrmann and H. Voss, Nonlinear eigenvalue problems: a challenge for modern eigenvalue methods, GAMM‐Mitteilungen 27.2 (2004): 121-152.
  * H. Voss and B. Werner, Solving sparse nonlinear eigenvalue problems. Technical Report 82/4, Inst. f. Angew. Mathematik, Universität Hamburg, 1982.
  * B. Werner. Das Spektrum von Operatorenscharen mit verallgemeinerten Rayleighquotienten. PhD thesis, Fachbereich Mathematik, Universität Hamburg, 1970

```
