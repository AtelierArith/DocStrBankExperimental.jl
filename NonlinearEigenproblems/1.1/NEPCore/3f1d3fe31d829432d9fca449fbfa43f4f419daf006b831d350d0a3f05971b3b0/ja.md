```
compute_Mlincomb(nep::NEP,λ::Number,V, a::Vector=ones(size(V,2)), startder=0)
compute_Mlincomb!(nep::NEP,λ::Number,V, a::Vector=ones(size(V,2)), startder=0)
```

導関数の線形結合を計算します $Σ_i a_i M^{(i)}(λ) v_i$ は導関数 `startder` から始まります。関数 `compute_Mlincomb!` は同じことを行いますが、`V` 行列/配列を変更する可能性があります。

# 例

この例は、`compute_Mder` が `compute_Mlincomb` と整合性のある結果を返すことを示しています。一般に、`compute_Mlincomb` は行列を構築する必要がないため、より高速です。

```julia-repl
julia> nep=nep_gallery("dep0");
julia> v=ones(size(nep,1)); λ=-1+1im;
julia> norm(compute_Mder(nep,λ,1)*v-compute_Mlincomb(nep,λ,hcat(v,v),[0,1]))
0.0
```
