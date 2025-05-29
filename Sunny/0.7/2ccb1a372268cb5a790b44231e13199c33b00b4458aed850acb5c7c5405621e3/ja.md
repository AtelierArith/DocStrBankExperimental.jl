```
set_onsite_coupling_at!(sys::System, op, site::Site)
```

単一の[`Site`](@ref)に対して、結晶対称性を無視して単一イオン異方性演算子`op`を設定します。システムは[`to_inhomogeneous`](@ref)を介して不均一な相互作用をサポートしている必要があります。

また、[`set_onsite_coupling!`](@ref)も参照してください。
