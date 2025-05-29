```
hardware_transform(h::BloqadeExpr.RydbergHamiltonian;device_capabilities::DeviceCapabilities=get_device_capabilities())
```

`device_capabilities`を介してハードウェアの制約を考慮し、`h`をマシンが実行可能な形に変換します。また、以下の情報も提供します：

  * 原子の元の位置と変換後の位置との間の平均二乗誤差
  * 元の波形と変換後の波形との間の1ノルムの差

これらはすべて[`HardwareTransformInfo`](@ref)構造体に格納されます。

`hardware_transform`は、すべての波形`h`に対して指定された(Ω, Δ, ϕ)が明示的に定義されていることを期待します。使用されていない波形がある場合は、非使用を示すために値がゼロの[`BloqadeWaveforms.constant`](@ref)波形を作成する必要があります。

すべての原子位置の制約が考慮されているわけではなく、最大格子幅、格子高さ、最小サポート間隔などが含まれていません。位置解像度のみが自動的に考慮されます。これにより、[`validation`](@ref)関数が失敗し、ユーザーが原子の位置を他の制約を満たすように修正する必要が生じる可能性があります。

# ログ/警告/例外

デバッグログは常に発生し、すべての波形(Ω, Δ, ϕ)にわたる元の波形と変換後の波形との間の差の1ノルムとして定義されるエラー、および元の原子位置と調整後の原子位置との間の平均二乗誤差を含みます。

構成関数[`hardware_transform_Ω`](@ref)、[`hardware_transform_Δ`](@ref)、[`hardware_transform_ϕ`](@ref)からのデバッグログ/警告も、`h`内の波形がそれらを引き起こす場合に発生します。

また、[`hardware_transform_atoms`](@ref)、[`hardware_transform_Ω`](@ref)、[`hardware_transform_Δ`](@ref)、[`hardware_transform_ϕ`](@ref)も参照してください。

# 例

```jldoctest; setup:=(using BloqadeExpr, BloqadeLattices)
julia> atom_positions = AtomList([(1.12,), (2.01,), (3.01,)]);

julia> Δ = Ω = ϕ = sinusoidal(duration=2, amplitude=1.3*π);

julia> h = rydberg_h(atom_positions; Ω=Ω,Δ=Δ,ϕ=ϕ)
nqubits: 3
+
├─ [+] ∑ 2π ⋅ 8.627e5.0/|x_i-x_j|^6 n_i n_j
├─ [+] Ω(t) ⋅∑ e^{ϕ(t) ⋅ im} |0⟩⟨1| + e^{-ϕ(t) ⋅ im} |1⟩⟨0|
└─ [-] Δ(t) ⋅ ∑ n_i


julia> hardware_transform(h)
(nqubits: 3
+
├─ [+] ∑ 2π ⋅ 8.627e5.0/|x_i-x_j|^6 n_i n_j
├─ [+] Ω(t) ⋅∑ e^{ϕ(t) ⋅ im} |0⟩⟨1| + e^{-ϕ(t) ⋅ im} |1⟩⟨0|
└─ [-] Δ(t) ⋅ ∑ n_i
, BloqadeSchema.HardwareTransformInfo(0.5386117854062276, 2.632451578170084, 0.06492452289703464, (Δ = Waveform(_, 2), δ = nothing, Δi = 1.0), 0.013333333333333197))
```
