```
function REP(A,roots,poles)
```

`REP`呼び出しは、有理固有値問題を作成します。`REP`は、$Σ_i A_i s_i(λ)/q_i(λ)$の和によって定義され、ここでi = 0,1,2,...、すべての行列はサイズ$n×n$であり、$s_i$と$q_i$は多項式です。コンストラクタは、最高係数が正規化された多項式の根と極を入力として受け取ります。NEPは次のように定義されます。

$$
-λI+A_0+A_1\frac{p(λ)}{q(λ)}
$$

ここで、`p`は根`roots`を持ち、`q`は根`poles`を持ちます。

# 例

```julia-repl
julia> A0=[1 2; 3 4]; A1=[3 4; 5 6];
julia> nep=REP([A0,A1],[1,3], [4,5,6]);
julia> compute_Mder(nep,3)
2×2 Array{Float64,2}:
 Inf  Inf
 Inf  Inf
julia> (λ,x)=quasinewton(nep,v=[1;0])
(-0.3689603779201249 + 0.0im, Complex{Float64}[-2.51824+0.0im, 1.71283+0.0im])
julia> -λ*x+A0*x+A1*x*(λ-1)*(λ-3)/((λ-4)*(λ-5)*(λ-6))
2-element Array{Complex{Float64},1}:
 -2.5055998942313806e-13 + 0.0im
   1.318944953254686e-13 + 0.0im
```
