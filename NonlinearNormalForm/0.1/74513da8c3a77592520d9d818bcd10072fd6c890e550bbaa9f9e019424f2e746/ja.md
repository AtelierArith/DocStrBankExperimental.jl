```
Probe{S,T,U<:Union{Quaternion{T},Nothing},V<:Union{Matrix,Nothing},W<:Union{Nothing,Bool}}
```

トラッキングに使用されるパラメトリック型です。軌道/スピン部分はスカラーまたは `TPS` を含むことができます。スピンが含まれている場合、フィールド `Q` は `x` と同じ型の `Quaternion` であり、そうでない場合は `Q` は `nothing` です。放射が含まれている場合、フィールド `E` には `eltype(E)==S` の FD 行列が含まれ、そうでない場合は `E` は `nothing` です。

すべての平面が擬似調和振動を示している場合、`idpt` は `nothing` です。最後の平面がコースティングしている場合、`idpt` は最後の平面でどの変数が定数（エネルギーのような）であるかを指定します：インデックス `NV-1` の変数が定数である場合は `idpt=false`、またはインデックス `NV` の変数が定数である場合は `idpt=true` です。
