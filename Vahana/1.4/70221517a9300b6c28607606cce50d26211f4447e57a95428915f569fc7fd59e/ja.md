```
write_snapshot(sim::Simulation, [comment::String = ""; ignore = []])
```

シミュレーション `sim` の現在の状態を添付された HDF5 ファイルに書き込みます。`comment` は [`list_snapshots`](@ref) を介してスナップショットを識別するために使用でき、この関数の `comment` キーワードを利用して [`read_snapshot!`](@ref) 関数を介してこのスナップショットを読み取ることができます。

`ignore` は、書き込まないべきエージェントおよび/またはエッジタイプのリストです。

関連情報としては、[`create_h5file!`](@ref)、[`read_snapshot!`](@ref) があります。
