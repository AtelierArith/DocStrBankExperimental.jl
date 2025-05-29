```
apply_noise(smld::BasicSMLD, σ_psf::Vector{<:AbstractFloat})
```

光子数に基づいて3Dエミッタの位置に局所化不確実性を追加します。

# 引数

  * `smld::BasicSMLD`: 3Dエミッタを含む入力SMLD
  * `σ_psf::Vector{<:AbstractFloat}`: マイクロメートル単位のPSF幅 [σx, σy, σz]

# 戻り値

  * `BasicSMLD`: ノイズのある位置と更新された不確実性を持つ新しいSMLD

# 例

```julia
# その後、特定のPSF幅で局所化ノイズを追加します
σ_psf = [0.13, 0.13, 0.39]  # 130nm横方向、390nm軸方向
smld_noisy = apply_noise(smld_model, σ_psf)
```
