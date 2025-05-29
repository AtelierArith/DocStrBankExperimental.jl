```
free_propagation(ψ, x, y, z [, scaling]; k=1)
```

初期プロファイル `ψ` を伝播させます。

伝播は、初期条件 `ψ` の下で距離 `z` における `∇² ψ + 2ik ∂_z ψ = 0` の解です。

`x` と `y` は `ψ` が計算されるグリッドです。

`z` が `AbstractArray` の場合、出力は `z` の各要素における解を表す3D配列です。

距離 `z[n]` における出力は、`scaling[n] * x` と `scaling[n] * y` で定義されたスケーリングされたグリッド上で計算されます。

`k` は波数です。

# 例

```jldoctest
x = LinRange(-10, 10, 256)
y = LinRange(-10, 10, 512)
z = LinRange(0.1, 1, 10)

ψ = hg(x, y; m=3, n=2)
ψ′ = hg(2x, 2y; m=3, n=2)

(
    free_propagation(ψ, x, y, z) ≈ stack(free_propagation(ψ, x, y, z) for z ∈ z)
    &&
    free_propagation(ψ, x, y, z, fill(2, length(z))) ≈ stack(free_propagation(ψ, x, y, z, 2) for z ∈ z)
    &&
    free_propagation(ψ, x, y, 0.5, 2) ≈ free_propagation(ψ′, 2x, 2y, 0.5)
)

# 出力
true
```
