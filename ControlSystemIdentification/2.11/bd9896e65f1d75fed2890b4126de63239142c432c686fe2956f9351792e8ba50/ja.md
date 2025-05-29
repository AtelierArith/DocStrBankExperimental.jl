```
prediction_error_filter(sys::AbstractPredictionStateSpace; h=1)
prediction_error_filter(sys::AbstractStateSpace, R1, R2; h=1)
```

`[u; y]`を入力として受け取り、予測誤差`e = y - ŷ`を出力するフィルタを返します。`innovation_form`および`noise_model`も参照してください。`h ≥ 1`は予測ホライズンです。`[u; y]`を入力として持つ`iddata`を生成するには、関数[`predictiondata`](@ref)を参照してください。
