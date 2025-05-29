```
test_opt(f, [types]; broken::Bool = false, skip::Bool = false, jetconfigs...)
test_opt(tt::Type{<:Tuple}; broken::Bool = false, skip::Bool = false, jetconfigs...)
```

指定された型シグネチャを持つ関数呼び出しに対して[`report_opt`](@ref)を実行し、`report_opt`が検出できる最適化の失敗や未解決のメソッドディスパッチがないことをテストします。呼び出し式ではなく型シグネチャを取るという点を除けば、この関数は[`@test_opt`](@ref)と同じように動作します。
