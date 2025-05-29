```
integrate!(ls::LevelSetEquation,tf,Δt=Inf)
```

[`LevelSetEquation`](@ref) `ls`を時間`tf`まで統合し、その過程でオブジェクト`ls`の`levelset`と`current_time`を変更します。

オプションのパラメータ`Δt`を渡すことで、統合のために許可される最大時間ステップを指定できます。内部で`tf`までレベルセットを進化させるために取られる時間ステップは、使用される`terms`や`integrator`に関連する安定性の理由から、`Δt`よりも小さい場合があることに注意してください。
