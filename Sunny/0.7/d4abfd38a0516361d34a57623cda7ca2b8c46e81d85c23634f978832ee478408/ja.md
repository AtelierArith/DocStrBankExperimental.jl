```
ssf_custom_bm(f, sys::System; u, v, apply_g=true, formfactors=nothing)
```

カスタム収縮関数 `f` を用いてスピン構造因子の測定を指定します。インターフェースは [`ssf_custom`](@ref) と同じですが、ここで `f` は運動量 $𝐪$ と Blume-Maleev 軸系の基底における 3×3 構造因子データ $\mathcal{S}^{αβ}(𝐪, ω)$ を受け取ります。逆格子単位で提供される波ベクトル `u` と `v` は散乱平面を定義するために使用されます。グローバルなカルテシアン座標系において、3つの直交する BM 軸 `(e1, e2, e3)` は次のように定義されます：

```julia
e3 = normalize(u × v)  # 散乱平面 (u, v) に対して法線
e1 = normalize(q)      # 散乱平面内の運動量移動 q
e2 = normalize(e3 × q) # q に垂直で散乱平面内
```

# 例

```julia
# 散乱平面 [0, K, L] における Blume-Maleev 軸系の S²³ - S³² の虚部を測定します。
measure = ssf_custom_bm(sys; u=[0, 1, 0], v=[0, 0, 1]) do q, ssf
    imag(ssf[2,3] - ssf[3,2])
end
```
