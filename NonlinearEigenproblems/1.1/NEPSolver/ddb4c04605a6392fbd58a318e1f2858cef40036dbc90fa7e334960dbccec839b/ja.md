```
compute_rf(eltype::Type,nep::NEP,x,inner_solver::InnerSolver;
           y=x, target=zero(T), λ=target,TOL=eps(real(T))*1e3,max_iter=10)
```

`nep`のレイリー関数を計算します。すなわち、$y^TM(λ)x=0$となる値$λ$のベクトル$Λ$を計算します。これは`inner_solver`で指定された手順を使用します。デフォルトの動作はスカラー値のニュートン反復から成り、返されるベクトルは1つの要素のみを持ちます。

与えられたeltype<:Numberは返されるベクトルの型です。

# 例

これは`iar`を使用して（スカラー）非線形問題を解決します。

```julia-repl
julia> nep=nep_gallery("dep0");
julia> x=ones(size(nep,1));
julia> s=compute_rf(ComplexF64,nep,x,IARInnerSolver())[1] # 最初の要素だけを取得
-1.186623627962043 - 1.5085094961223182im
julia> x'*compute_Mlincomb(nep,s,x)
-8.881784197001252e-16 + 1.0880185641326534e-14im
```
