```
hardware_transform_atoms(atoms,device_capabilities::DeviceCapabilities=get_device_capabilities())
```

`device_capabilities`からのハードウェアの制約（特に位置解像度）と、原子の位置を含むイテラブル`atoms`を考慮して、機械が解決可能な調整された原子位置と、望ましい原子位置と新たに生成された位置との間の平均二乗誤差を含むタプルを返します。

最大幅、高さ、最小サポート間隔などの他の制約は、原子の調整には考慮されていないことに注意してください。これにより、[`validation`](@ref) 関数が失敗し、ユーザーが原子の位置を修正して他の制約を満たす必要が生じる可能性があります。

# 例

```jldoctest;
julia> atom_positions = ((1.12,), (2.01,), (3.01,));

julia> hardware_transform_atoms(atom_positions) # デフォルトでは、get_device_capabilities()を呼び出します
([(1.1,), (2.0,), (3.0,)], 0.013333333333333197)
```
