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

Returns a tuple of the IPA settings, with defaults for everything except dims. This can be passed to the IPA and IPCrossAStructureModuleLayer.
