```
enable_dipole_dipole!(sys::System, μ0_μB²)
```

磁気双極子モーメント間の長距離相互作用を有効にします。

$$
    -(μ_0/4π) ∑_{⟨ij⟩}  [3 (μ_i⋅𝐫̂_{ij})(μ_j⋅𝐫̂_{ij}) - μ_i⋅μ_j] / r_{ij}^3,
$$

ここで、和はすべてのサイトのペア（単独でカウント）にわたるもので、周期的な画像を含み、エヴァルド和の規則を使用して正則化されています。各磁気モーメントは $μ = -g μ_B 𝐒$ であり、$𝐒$ はスピン角運動量双極子です。パラメータ `μ0_μB²` は物理定数 $μ_0 μ_B^2$ を指定し、これは長さ³-エネルギーの次元を持ちます。この定数は、[`Units`](@ref) の `vacuum_permeability` プロパティを介して、与えられたシステムのために取得できます。

# 例

```julia
units = Units(:meV, :angstrom)
enable_dipole_dipole!(sys, units.vacuum_permeability)
```

!!! tip "効率に関する考慮事項"
    磁気双極子相互作用は、スピンダイナミクスシミュレーションの文脈では非常に効率的です。例えば、[`Langevin`](@ref) では、スピンに対して各ブラヴァイサブ格子上で高速フーリエ変換（FFT）を適用し、1つのタイムステップを統合するための計算コストは $M^2 N \ln N$ のようにスケールします。ここで、$N$ はシステム内のセルの数、$M$ はセルあたりのブラヴァイサブ格子の数です。逆に、磁気双極子相互作用は [`LocalSampler`](@ref) の文脈では非常に*非効率的*です。現在、単一スピンの各モンテカルロ更新は、システム内の他のすべてのスピンをスキャンする必要があります。


[`modify_exchange_with_truncated_dipole_dipole!`](@ref) も参照してください。
