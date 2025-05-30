```
D_matrices!(D_storage, R)
D_matrices!(D_storage, α, β, γ)
D_matrices!(D, R, ℓₘₐₓ)
D_matrices!(D, α, β, γ, ℓₘₐₓ)
```

ウィグナーの 𝔇 行列 $\mathfrak{D}^{(\ell)}_{m',m}(\beta)$ をすべての $\ell \leq \ell_\mathrm{max}$ に対して計算します。

すべての場合において、結果は次のように順序付けられた 1 次元配列で返されます。

```
[
    𝔇ˡₘₚ,ₘ(R)
    for ℓ ∈ 0:ℓₘₐₓ
    for mp ∈ -ℓ:ℓ
    for m ∈ -ℓ:ℓ
]
```

最初の引数が `D` の場合、それは変更されるため、その配列と同じかそれ以上の大きさでなければなりません。最初の引数が `D_storage` の場合、それは [`D_prep`](@ref) によって返される量であり、そのタプルの `D` フィールドに結果が書き込まれます。これらのオプションは、特に後者は、対応する関数への各呼び出しで必要な割り当ての数を減らし、速度を大幅に向上させるはずです。`D` または `D_storage` 引数は、`R` または `α, β, γ` の型と互換性のある型でなければなりません。

!!! warn
    `D_storage` 引数を使用する場合（推奨）、返される量 `D` は `D_storage[1]` のエイリアスになります。次の [`D_matrices!`](@ref) の呼び出し後にそのデータを保持したい場合は、`copy(D)` を使用してコピーする必要があります。


`α, β, γ` 引数は、[`Quaternionic.from_euler_angles`](https://moble.github.io/Quaternionic.jl/dev/manual/#Quaternionic.from_euler_angles-Tuple{Any,%20Any,%20Any}) のドキュメントに記載されているようにオイラー角です。

単一の値の `R` または `α, β, γ` に対して行列を評価するだけの場合は、より簡単な関数呼び出しのために [`D_matrices`](@ref) も参照してください。

# 例

```julia
using Quaternionic, SphericalFunctions
ℓₘₐₓ = 8
T = Float64
R = Rotor{T}(1, 2, 3, 4)  # 自動的に正規化されます
D_storage = D_prep(ℓₘₐₓ, T)
D = D_matrices!(D_storage, R)
```
