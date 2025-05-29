```
res = lsim!(ws::LsimWorkspace, sys::AbstractStateSpace{<:Discrete}, u, [t]; x0)
```

[`lsim`](@ref) のインプレースバージョンで、[`LsimWorkspace`](@ref) を呼び出して作成されたワークスペースオブジェクトを取ります。*注意*、もし `u` が関数であれば、`res.u === ws.u` になります。もし `u` が配列であれば、`res.u === u` になります。
