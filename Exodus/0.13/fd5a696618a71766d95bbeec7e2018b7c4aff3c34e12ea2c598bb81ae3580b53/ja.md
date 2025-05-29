```julia
ExodusDatabase(
    file_name::String,
    mode::String
) -> Exodus.ExodusDatabase{_A, _B, _C, _D, Exodus.Initialization{ND, NN, NE, NEB, NNS, NSS}} where {_A, _B, _C, _D, ND, NN, NE, NEB, NNS, NSS}

```

型の安定性を得るために煩わしいコード行を排除するための型不安定なヘルパー。

エクソダスファイルを開くための型安定な方法を探している場合は、これをバリア関数にコピー＆ペーストしてください。
