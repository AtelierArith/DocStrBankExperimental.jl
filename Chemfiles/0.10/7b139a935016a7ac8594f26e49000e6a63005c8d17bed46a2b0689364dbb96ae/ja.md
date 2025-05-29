```julia
MemoryTrajectory(
    format::AbstractString
) -> Chemfiles.Trajectory
MemoryTrajectory(
    format::AbstractString,
    data::Union{Nothing, AbstractString, Vector{UInt8}}
) -> Chemfiles.Trajectory

```

メモリ内のデータをフォーマットされたファイルのように読み込むトラジェクトリを開きます。

データの `format` は必須であり、既知のフォーマットのいずれかと一致する必要があります。`data` が `nothing` の場合、この関数はメモリライターを作成し、結果のデータは `buffer` で取得できます。そうでない場合、この関数は指定されたデータを使用してメモリリーダーを作成します。
