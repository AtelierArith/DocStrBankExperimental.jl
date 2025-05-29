```
write_vtk(name, assembly::Assembly; kwargs...)
write_vtk(name, assembly::Assembly, state::AssemblyState; kwargs...)
write_vtk(name, assembly::Assembly, history::Vector{<:AssemblyState}], dt;
    kwargs...)
```

変形したジオメトリ（および関連データ）をVTKファイルに書き込み、ParaViewを使用して視覚化します。

`state`引数は省略可能で、関連データなしで元のジオメトリをVTKファイルに書き込むことができます。

解の時間`history`が提供される場合、タイムステップも提供する必要があります。

# キーワード引数

  * `sections = nothing`: 各点に対応する断面ジオメトリで、ボディフレームに沿ったフレームで定義され、対応する点の周りに中心を置いています。形状が`(3, ncross, np)`の配列として定義され、`ncross`は各断面の点の数、`np`は点の数です。
  * `scaling=1.0`: 変位をスケーリングするためのパラメータ（stateが提供されている場合のみ有効）
  * `metadata=Dict()`: ファイルのメタデータの辞書
