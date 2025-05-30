```
sYlm_values!(sYlm_storage, R, spin)
sYlm_values!(sYlm_storage, θ, ϕ, spin)
sYlm_values!(sYlm, R, ℓₘₐₓ, spin)
sYlm_values!(sYlm, θ, ϕ, ℓₘₐₓ, spin)
```

スピン加重球面調和関数 ${}_{s}Y_{\ell, m}(R)$ の値をすべての $\ell \leq \ell_\mathrm{max}$ に対して計算します。

スピン重み $s$ の球面調和関数は、ウィグナーの $\mathfrak{D}$ 行列に関連しています。

$$
\begin{aligned}
{}_{s}Y_{\ell, m}(R)
  &= (-1)^s \sqrt{\frac{2\ell+1}{4\pi}} \mathfrak{D}^{(\ell)}_{m, -s}(R) \\
  &= (-1)^s \sqrt{\frac{2\ell+1}{4\pi}} \bar{\mathfrak{D}}^{(\ell)}_{-s, m}(\bar{R}).
\end{aligned}
$$

すべての場合において、結果は次のように順序付けられた1次元配列で返されます。

```
[
    ₛYₗₘ(R)
    for ℓ ∈ 0:ℓₘₐₓ
    for m ∈ -ℓ:ℓ
]
```

最初の引数が `Y` の場合、それは変更されるため、その配列と同じかそれ以上の大きさでなければなりません。最初の引数が `sYlm_storage` の場合、それは [`sYlm_prep`](@ref) によって返される量であり、結果はそのタプルの `Y` フィールドに書き込まれます。これらのオプションの両方、特に後者は、対応する関数への各呼び出しで必要な割り当ての数を減らし、速度を大幅に向上させるはずです。`Y` または `sYlm_storage` 引数は、`R` または `θ, ϕ` の型と互換性のある型でなければなりません。

!!! warn
    `sYlm_storage` 引数を使用する場合（推奨）、返される量 `sYlm` は `sYlm_storage[1]` のエイリアスになります。次の [`sYlm_values!`](@ref) の呼び出し後にそのデータを保持したい場合は、`copy(sYlm)` でコピーする必要があります。


`θ, ϕ` 引数は、[`Quaternionic.from_spherical_coordinates`](https://moble.github.io/Quaternionic.jl/dev/manual/#Quaternionic.from_spherical_coordinates-Tuple{Any,%20Any}) のドキュメントに記載されている球面座標です。

単一の `R` または `θ, ϕ` の値に対して ${}_{s}Y_{\ell, m}$ を評価する必要がある場合は、より簡単な関数呼び出しのために [`sYlm_values`](@ref) も参照してください。

# 例

```julia
using Quaternionic, SphericalFunctions
spin = -2
ℓₘₐₓ = 8
T = Float64
R = Rotor{T}(1, 2, 3, 4)  # 自動的に正規化されます
sYlm_storage = sYlm_prep(ℓₘₐₓ, spin, T)
sYlm = sYlm_values!(sYlm_storage, R, spin)
```
