```
write_tepfile(filename::AbstractString, tep::TEP)
write_tepfile(filename::AbstractString, tep::Vector{TEPscatter})
```

TICRA互換の「表形式電気特性」(TEP)ファイルを書きます。 `type(tep) == TEPscatter` または `type(tep) == Vector{TEPscatter}` の場合、ファイルはGRASP8によって導入された元の形式（散乱面）で書き込まれます。 `type(tep) == TEPperiodic` の場合、ファイルはQUPESプログラムによって導入された周期的ユニットセルの新しい形式で書き込まれます。
