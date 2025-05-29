```
dnep=deflate_eigpair(orgnep::NEP,λ,v,[mode=:Auto])
```

この関数は、`nep`の固有対と仮定される$(λ,v)$に基づいて、除去されたNEPを作成します。実際には、関数は`dnep::NEP`を返し、これはorgnepと同じ解を持ちますが、$(λ,v)$に対応する解は除外されます。除去は通常、再収束を避けるために使用されます。

`orgnep`が`DeflatedNEP`である場合、`orgnep`の除去は更新されます。

`mode`キーワード引数は、`:Auto`、`:Generic`、`:SPMF`、`:MM`のいずれかに設定できます。これは、除去されたNEPがどのように表現されるべきかを指定します。どのモードが最も効率的かは、多くの問題の特性に依存します。元のNEPが項が少ない`AbstractSPMF`である場合、`mode=:SPMF`が効率的である可能性があります。SPMFモードは、除去された不変対の対角化に基づいており、近接する固有値を除去する際には必ずしも堅牢ではありません。`mode=:MM`が使用されると、すべての計算関数は`compute_MM`への呼び出しを介して実装されます。これは、小さな密な問題に対してうまく機能することがあります。`:Generic`は、問題の明示的な導出（二項展開を介して）に基づいており、低次の導関数が必要な場合に効率的である可能性があります。`:Auto`が選択されると、NEP-PACKは`orgnep`に基づいてどれが最も効率的かを判断しようとします。

# 例:

```julia-repl
julia> nep=nep_gallery("dep0");
julia> (λ,v)=newton(nep,v=ones(size(nep,1)));
julia> dnep=deflate_eigpair(nep,λ,v)
julia> (λ2,v2)=augnewton(dnep,v=ones(size(dnep,1)));  # これは異なる固有値に収束します
julia> using LinearAlgebra;
julia> minimum(svdvals(compute_Mder(nep,λ2)))
2.5161012836775824e-17
```

関数[`get_deflated_eigpairs()`](@ref)は、除去された固有対を抽出します。返される対は、元のNEPの固有対です：

```julia-repl
julia> dnep=deflate_eigpair(dnep,λ2,v2);
julia> (D,V)=get_deflated_eigpairs(dnep)
julia> norm(compute_Mlincomb(nep,D[1],V[:,1]))
2.3970746442479104e-16
julia> norm(compute_Mlincomb(nep,D[2],V[:,2]))
8.101585801848734e-16
```

# 参考文献

  * C. Effenberger, Robust solution methods for nonlinear eigenvalue problems, PhD thesis, 2013, EPF Lausanne

```
