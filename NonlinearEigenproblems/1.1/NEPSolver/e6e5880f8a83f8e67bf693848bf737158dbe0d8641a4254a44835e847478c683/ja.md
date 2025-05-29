```
λ,v = resinv([eltype],nep::NEP;[errmeasure,][tol,][maxit,][λ,][v,][c,][logger,][armijo_factor=1,][armijo_max,][linsolvecreator])
```

非線形固有値問題に対する残差逆反復法を適用します。キーワード引数 `linsolvecreator` は、線形系がどのように作成されるかを指定する関数です。この関数は、レイリー関数の計算のために `compute_rf` を呼び出します。他のパラメータについては [`augnewton`](@ref) を参照してください。

# 例

この例では、メソッドが実数モードまたは複素数モード（または他の `Number` 型）で実行されるべきかを指定する方法を示します。

```julia-repl
julia> nep=nep_gallery("qdep0");
julia> λ,v=resinv(nep,λ=-2,v=ones(size(nep,1)))
julia> typeof(λ)
Complex{Float64}
julia> norm(compute_Mlincomb(nep,λ,v))
6.688224435370382e-12
julia> λ,v=resinv(Float64,nep,λ=-2,v=ones(size(nep,1)))
julia> typeof(λ)
Float64
julia> norm(compute_Mlincomb(nep,λ,v))
5.939894690000396e-12
```

# 参考文献

  * A. Neumaier, 非線形固有値問題のための残差逆反復法, SIAM J. Numer. Anal. 22 (1985) 914-923
