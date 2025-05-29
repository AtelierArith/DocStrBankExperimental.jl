```julia
set_topology!(
    trajectory::Chemfiles.Trajectory,
    path::AbstractString
)
set_topology!(
    trajectory::Chemfiles.Trajectory,
    path::AbstractString,
    format::AbstractString
)

```

`trajectory`に関連付けられた`Topology`を、`path`のファイルの最初のフレームを読み込むことによって設定し、このフレームのトポロジーを抽出します。オプションの`format`パラメータを使用して、ファイル形式を指定することができます。
