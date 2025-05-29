```
apply_noise(smld::BasicSMLD, σ_psf::AbstractFloat)
```

光子数に基づいて2Dエミッタの位置に局所化不確実性を追加します。

# 引数

  * `smld::BasicSMLD`: 2Dエミッタを含む入力SMLD
  * `σ_psf::AbstractFloat`: マイクロメートル単位のPSF幅

# 戻り値

  * `BasicSMLD`: ノイズのある位置と更新された不確実性を持つ新しいSMLD

# 例

```julia
# その後、特定のPSF幅で局所化ノイズを追加します
smld_noisy = apply_noise(smld_model, 0.13)  # 130nm PSF幅
```
