```
IPA_settings(
    dims;
    c = 16,
    N_head = 12,
    N_query_points = 4,
    N_point_values = 8,
    c_z = 0,
    Typ = Float32,
    use_softmax1 = false,
    scaling_qk = :default,
)
```

すべてのデフォルトを除いてdimsのデフォルトを持つIPA設定のタプルを返します。これはIPAおよびIPCrossAStructureModuleLayerに渡すことができます。
