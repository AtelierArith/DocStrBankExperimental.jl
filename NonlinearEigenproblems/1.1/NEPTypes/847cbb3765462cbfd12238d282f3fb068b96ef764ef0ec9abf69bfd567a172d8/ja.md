```
ChebPEP(orgnep::NEP,k,[a=-1,[b=1]] [,cosine_formula_cutoff=5])
```

型 `ChebPEP<:AbstractSPMF` は、関数が区間 `[a,b]` にスケーリングされたチェビシェフ基底を使用して保存される多項式関数を表します。すなわち、

$$
M(λ)= B_0T_0(λ)+⋯+B_{k-1}T_{k-1}(λ)
$$

ここで $T_i$ はスケーリングされ、シフトされたチェビシェフ多項式です。

コンストラクタ `ChebPEP` は `nep::NEP` を入力として受け取り、この NEP を `k` チェビシェフノードで補間し、チェビシェフ基底の係数で表される次数 `k-1` の多項式を生成します。チェビシェフノードでの補間とチェビシェフ基底による表現は、魅力的な近似特性を持ち、丸め誤差に対しても堅牢であることが知られています。

キーワード引数 `cosine_formula_cutoff` は、チェビシェフ多項式がどのように計算されるべきかを決定します。次数が大きい場合はコサイン公式を使用する方が良く、低い次数の場合は明示的な単項式表現の方が効率的です。明示的な単項式表現は `cosine_formula_cutoff` よりも低い次数に対して使用されます。

# 例:

```julia
julia> nep=nep_gallery("dep0");
julia> chebpep=ChebPEP(nep,9);
julia> using LinearAlgebra;
julia> norm(compute_Mder(nep,0.3)-compute_Mder(chebpep,0.3))
1.2881862971045282e-8
julia> chebpep=ChebPEP(nep,19); # より良い補間
julia> norm(compute_Mder(nep,0.3)-compute_Mder(chebpep,0.3))
2.0312004517316714e-15
```

参照: [`polyeig`](methods.md#NonlinearEigenproblems.NEPSolver.polyeig), [`PEP`](@ref)
