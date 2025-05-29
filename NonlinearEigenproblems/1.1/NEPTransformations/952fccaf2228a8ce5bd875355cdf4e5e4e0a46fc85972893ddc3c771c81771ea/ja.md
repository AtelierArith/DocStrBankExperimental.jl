```
shift_and_scale(orgnep::NEP;shift=0,scale=1)
```

orgnepを変換し、T(λ)=M(scale * λ+shift)の関係から新しいNEPを定義します。ここでMはorgnepです。この関数はNEPタイプを保持しようとします。たとえば、SPMFオブジェクトに対するshift*and*scale操作は、SPMFオブジェクトを返します。タイプを保持できない場合は、構造体`ShiftScaledNEP`のnepを返します。

# 例

```julia-repl
julia> nep0=nep_gallery("pep0")
julia> σ=3; α=10;
julia> nep1=shift_and_scale(nep0,shift=σ,scale=α)
julia> opnorm(compute_Mder(nep0,α*(4+4im)+σ)-compute_Mder(nep1,4+4im))
8.875435870738592e-12
```
