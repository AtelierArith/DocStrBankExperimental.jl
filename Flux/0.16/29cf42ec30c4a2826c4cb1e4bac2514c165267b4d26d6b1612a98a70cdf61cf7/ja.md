```
testmode!(model, [mode]) -> model
```

モデル内のレイヤー、またはすべてのレイヤーをテストモードに設定します。これにより、[`Dropout`](@ref)やその他の正則化レイヤーの効果が無効になります。

モデルを手動でテストモードに設定した場合、トレーニングフェーズ中に手動でトレインモードに戻す必要があります。これは[`trainmode!`](@ref)を使用して行います。

オプションの第二引数があり、シンボル`:auto`を指定すると、すべてのレイヤーをデフォルトの自動モードにリセットします。

# 例

```jldoctest
julia> d = Dropout(0.3)
Dropout(0.3)

julia> testmode!(d)   # dropoutは現在常に無効
Dropout(0.3, active=false)

julia> trainmode!(d)  # dropoutは現在常に有効
Dropout(0.3, active=true)

julia> testmode!(d, :auto)  # デフォルトに戻る
Dropout(0.3)
```
