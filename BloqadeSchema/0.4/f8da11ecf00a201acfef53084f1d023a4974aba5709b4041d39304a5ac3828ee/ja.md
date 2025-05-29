```
get_device_capabilities(capabilities_file=nothing)
```

明示的に提供された能力 JSON ファイルへのパスを使用するか、デフォルトの JSON を使用して `DeviceCapabilities` 構造体を生成します。デフォルトでは、能力 JSON ファイルの単位は "lib/BloqadeSchema/config/capabilities-qpu1-mock-units.json" ファイルによって指定され、この関数は *非SI基本*（例：μm、μs）単位の `DeviceCapabilities` 構造体を返します。

また、[`get_device_capabilities_SI`](@ref) も参照してください。

```jldoctest;
julia> get_device_capabilities()
BloqadeSchema.DeviceCapabilities(BloqadeSchema.TaskCapabilities(1, 1000), BloqadeSchema.LatticeCapabilities(BloqadeSchema.LatticeAreaCapabilities(75.0, 76.0), BloqadeSchema.LatticeGeometryCapabilities(4.0, 4.0, 0.1, 256), 256), BloqadeSchema.RydbergCapabilities(5.42e6, BloqadeSchema.RydbergGlobalCapabilities(0.0, 15.8, 0.0004, 250.0, -125.0, 125.0, 2.0e-7, 2500.0, -99.0, 99.0, 5.0e-7, 0.0, 4.0, 0.001, 0.05), nothing))
```
