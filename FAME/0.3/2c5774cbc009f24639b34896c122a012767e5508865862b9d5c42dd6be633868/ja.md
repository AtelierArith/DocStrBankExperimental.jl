```
mutable struct FameObject{CL,FT,FR,DT} … end
```

クラス `CL`、タイプ `FT`、周波数 `FR`、データタイプ `DT` の FAME オブジェクト。

`FameObject` は [`quick_info`](@ref) によって返され、`FameObject` のベクターは [`listdb`](@ref) によって返されます。

また、`FameObject` は `FameObject(name, class, type, frequency)` または `FameObject(name, class, type, frequency, first_index, last_index)` を呼び出すことで直接構築できます。`class`、`type`、および `frequency` の値はシンボル（例えば、`:scalar`、`:precision` など）または整数であることができます。コード値については FAME CHLI ドキュメントを参照してください。
