```
cl2dl(cl::AbstractVector{T}, lmin::Integer) where {T <: Real}
```

$$
C_{\ell}
$$

から $D_{\ell}$ パワースペクトルへの変換。ここで、$D_{\ell} = \ell (\ell + 1) C_{\ell} / 2\pi$。最初の成分は存在しない場合はゼロに設定されます。

# 引数:

  * `cl::AbstractVector{T}` : C_ℓ 成分の配列
  * `lmin::Integer` : C_ℓ パワースペクトルの表現における最小 l

# 戻り値:

  * `Vector{T}` : D_ℓ パワースペクトル成分の配列
