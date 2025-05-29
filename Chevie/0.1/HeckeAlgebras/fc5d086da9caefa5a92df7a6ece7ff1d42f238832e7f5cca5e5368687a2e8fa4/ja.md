`factorized_schur_elements(H)`

`H` を複素反射群 `W` のヘッケ代数とし、そのパラメータはすべて変数 `x₁,…,xₙ` の (ローレンツ) モノミアルであるとします。また、`K` を `W` の定義体とします。マリア・クローヴェラキは、`H` のシュール要素が `M ∏ᵩ φ(Mᵩ)` という特定の形を取ることを示しました。ここで `φ` は K-サイクリック多項式のリストを走り、`M` と `Mᵩ` は変数 `xᵢ` の (ローレンツ) モノミアル（おそらくいくつかの分数冪を含む）です。関数 `factorized_schur_elements` は、この因数分解を示すデータ構造（`HeckeAlgebras.FactSchur` を参照）を返します。

```julia-repl
julia> W=complex_reflection_group(4)
G₄

julia> @Mvp x,y; H=hecke(W,[[1,x,y]])
hecke(G₄,Vector{Mvp{Int64, Int64}}[[1, x, y]])

julia> factorized_schur_elements(H)
7-element Vector{Chevie.HeckeAlgebras.FactSchur}:
 x⁻⁴y⁻⁴(xy+1)Φ₁Φ₆(x)Φ₁Φ₆(y)
 (x²y⁻¹+1)Φ₁Φ₆(x)Φ₁Φ₆(xy⁻¹)
 -x⁻⁴y⁵Φ₁Φ₆(xy⁻¹)(xy⁻²+1)Φ₁Φ₆(y)
 -x⁻¹y(xy+1)(x-1)Φ₆(xy⁻¹)(y-1)
 -x⁻⁴y(x²y⁻¹+1)(x-1)(xy⁻¹-1)Φ₆(y)
 x⁻¹y⁻¹Φ₆(x)(xy⁻¹-1)(xy⁻²+1)(y-1)
 x⁻²y(x²y⁻¹+1)(xy+1)(xy⁻²+1)
```
