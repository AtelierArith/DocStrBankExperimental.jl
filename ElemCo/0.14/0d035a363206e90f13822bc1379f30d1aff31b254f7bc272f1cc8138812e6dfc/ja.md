```
@ECinit()
```

`EC::ECInfo`を初期化し、変数`geometry::String`および`basis::Dict{String,Any}`、および/または`fcidump::String`が定義されている場合は分子系および/またはfcidumpを追加します。

`EC`がすでに初期化されている場合は、上書きされます。

# 例

```julia
geometry="He 0.0 0.0 0.0"
basis = Dict("ao"=>"cc-pVDZ", "jkfit"=>"cc-pvtz-jkfit", "mpfit"=>"cc-pvdz-mpfit")
@ECinit
# 出力
Occupied orbitals:[1]

```
