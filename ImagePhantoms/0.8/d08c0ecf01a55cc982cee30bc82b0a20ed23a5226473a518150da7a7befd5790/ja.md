```
mri_smap_fit(smaps, embed ; mask, kwargs...)
```

MRI感度マップ`smaps`を`mri_smap_basis(mask ; kwargs...)`を使用してフィットします。呼び出し元は`ImageGeoms.embed`または同等のものを提供します。

名前付きタプル`(B, ν, coefs, nrmse, smaps)`を返します：

  * `(B, ν)`は`mri_smap_basis`から
  * `coefs::Vector` : `[ncoil]` 各要素の長さは`nk`
  * `nrmse::Real` : `smaps`と`smaps_fit`の比較
  * `smaps::Vector{Array{D}}` : `smaps_fit`

```
