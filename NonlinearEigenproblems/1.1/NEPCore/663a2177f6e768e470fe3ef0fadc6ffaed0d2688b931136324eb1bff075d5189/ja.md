```
compute_Mder(nep::NEP,λ::Number [,i::Integer=0])
```

`nep`の`λ`で評価されたi番目の導関数を計算します。

# 例

この例は、`compute_Mder(nep,λ,1)`が最初の導関数を与えることを示しています。

```julia-repl
julia> nep=nep_gallery("dep0");
julia> ϵ=1e-5; λ=2.25;
julia> Aminus=compute_Mder(nep,λ-ϵ);
julia> Aplus=compute_Mder(nep,λ+ϵ);
julia> opnorm((Aplus-Aminus)/(2ϵ)-compute_Mder(nep,λ,1))
1.8783432885257602e-11
```
