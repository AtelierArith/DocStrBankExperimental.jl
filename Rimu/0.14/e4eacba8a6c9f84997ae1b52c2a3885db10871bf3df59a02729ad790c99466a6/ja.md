```
RunTillLastStep(step::Int = 0 # 現在/開始のタイムステップの数
             laststep::Int = 100 # 最終タイムステップの数
             shiftMode::Bool = false # シフトを調整するかどうか
             shift = 0.0 # シフトの開始/現在の値
             dτ::Float64 = 0.01 # 現在の時間ステップの値
) <: FciqmcRunStrategy
```

固定されたタイムステップ数で[`lomc!()`](@ref)を実行するためのパラメータ。代替戦略については、[`FciqmcRunStrategy`](@ref)を参照してください。

!!! warning
    この戦略の使用は非推奨です。関連する引数を直接[`ProjectorMonteCarloProblem`](@ref)または[`lomc!()`](@ref)に渡してください。

