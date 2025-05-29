```
struct CORKPencil
function CORKPencil(M,N,Av,Bv,Z);
function CORKPencil(nep,is)
```

構造体 `CORKPencil` は、参照に示されている特定の構造を持つ鉛筆を表します。データは、最初のコンストラクタを介して直接構築することも、2番目のコンストラクタを介して NEP から構築することもできます。2番目のコンストラクタは、CORK 構造を指定する `NEP` と `is` を受け取ります。また、`IarCorkLinearization` または `NleigsCorkLinearization` の型のオブジェクトである必要があります。これらは、[`iar`](@ref) および [`nleigs`](@ref) の（特定のバージョンに相当する）CORK 線形化です。

標準的な鉛筆を構築する方法については、[`buildPencil`](@ref) を参照してください。

# 例:

以下の例では、一般的な NEP から `CORKPencil` を構築し、その後 `nleigs` の補間アプローチによって NEP の近似を計算します。

```julia-repl
julia> using LinearAlgebra
julia> A=(1:4)*(1:4)'+I; B=diagm(1 => [1,2,3]); C=ones(4,4);
julia> f1= λ-> one(λ);
julia> f2= λ-> λ;
julia> f3= λ-> exp(sin(λ/2));
julia> nep=SPMF_NEP([A,B,C],[f1,f2,f3]);
julia> cp=CORKPencil(nep,NleigsCorkLinearization());
julia> (A,B)=buildPencil(cp) # Form the pencil
julia> λv=eigen(A,B).values;
julia> λ=λv[sortperm(abs.(λv))[1]]; # Smallest eigval
julia> minimum(svdvals(compute_Mder(nep,λ))) # It's a solution
2.4364382475487156e-11
```

# 参考文献:

  * 非線形固有値問題のためのコンパクトな有理クライロフ法 SIAM Journal on Matrix Analysis and Applications, 36 (2), 820-838, 2015.

    ```
