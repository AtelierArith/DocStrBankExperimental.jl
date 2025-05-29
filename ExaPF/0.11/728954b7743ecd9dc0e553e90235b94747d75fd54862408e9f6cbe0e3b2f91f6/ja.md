```
PolarForm{T, IT, VT, MT} <: AbstractPolarFormulation
```

ネットワークの方程式に関連する極形式を実装します。

[`PS.PowerNetwork`](@ref) ネットワークをラップして、ターゲットデバイス（`CPU()` と `CUDABackend()` が現在サポートされています）にデータをロードします。

## 例

```jldoctest; setup=:(using ExaPF)
julia> const PS = ExaPF.PowerSystem;

julia> network_data = PS.load_case("case9.m");

julia> polar = PolarForm(network_data, ExaPF.CPU())
極形式 (デバイス CPU(false) にインスタンス化)
ネットワークの特性:
    #バス:      9  (#スラック: 1  #PV: 2  #PQ: 6)
    #発電機: 3
    #ライン:      9
次の数式を持つ数学的な定式化を提供します:
    #制御:   5
    #状態  :   14

```
