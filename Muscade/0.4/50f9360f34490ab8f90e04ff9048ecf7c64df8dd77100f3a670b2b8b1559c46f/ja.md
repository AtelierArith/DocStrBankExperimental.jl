```
initialstate = initialize!(model)
```

モデルの初期 `State` を返し、すべての自由度 (dofs) をゼロに設定します。

モデルを変更すること（`initialize!` の後に `addnode!` と `addelement!` を呼び出すこと）はエラーになります。

オプションのキーワード引数: `nΛder=1`, `nXder=1`, `nUder=1` は、`State` に保存する「導関数」の数を指定します。 "`n⋅der==order+1`" であることに注意してください。つまり、動的問題（加速度を含む）では、`nXder=3` となり、`order==2` です。 `n⋅der` を設定する必要があるのは、[`setdof!`](@ref) が使用される場合のみです。動的ソルバーは「静的」初期状態をうまく処理します。 `time=-∞` は初期状態に関連付けられた時間です。例えば、`time=0.` を設定し、その後に最初の時間ステップも `0.` でソルバーを呼び出すとエラーが発生します。

参照: [`setdof!`](@ref), [`Model`](@ref), [`addnode!`](@ref), [`addelement!`](@ref), [`solve`](@ref)
