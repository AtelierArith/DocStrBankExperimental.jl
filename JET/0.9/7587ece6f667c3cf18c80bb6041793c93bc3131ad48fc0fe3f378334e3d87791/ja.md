```
test_call(f, [types]; broken::Bool = false, skip::Bool = false, jetconfigs...)
test_call(tt::Type{<:Tuple}; broken::Bool = false, skip::Bool = false, jetconfigs...)
```

指定された型シグネチャを持つ関数呼び出しで[`report_call`](@ref)を実行し、`report_call`が検出できる問題がないことをテストします。呼び出し式ではなく型シグネチャを取るという点を除けば、この関数は[`@test_call`](@ref)と同じように動作します。
