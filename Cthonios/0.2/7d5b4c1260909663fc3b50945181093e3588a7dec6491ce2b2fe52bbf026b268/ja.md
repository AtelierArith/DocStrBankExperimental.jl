```julia
ExodusPostProcessor(
    mesh_file::String,
    output_file::String,
    solution_fields::Vector{String}
) -> Cthonios.ExodusPostProcessor{Exo} where Exo<:(Exodus.ExodusDatabase{_A, _B, _C, _D, Exodus.Initialization{ND, NN, NE, NEB, NNS, NSS}} where {_A, _B, _C, _D, ND, NN, NE, NEB, NNS, NSS})

```

`ExodusPostProcessor`のコンストラクタ。`mesh_file` - コピーするメッシュファイルの名前。`output_file` - メッシュをコピーするファイルの名前。`solution_fields` - ノード解フィールドの名前。
