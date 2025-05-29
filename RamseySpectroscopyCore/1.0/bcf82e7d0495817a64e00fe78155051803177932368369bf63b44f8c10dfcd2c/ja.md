```
pump(state_vector::StateVector, pulse::PerturbEvol) -> StateVector
```

レーザーパルスの存在下でのシステムの進化に従って量子システムの状態を変換します。

# 引数

  * `state_vector` :   量子システムの現在の状態ベクトル。
  * `pulse` :   量子システムに適用されるレーザーパルス。

# 戻り値

  * `StateVector` :   変換された `state` オブジェクトを持つ複合型インスタンス。

# 参照

  * [`StateVector`](@ref)
  * [`PerturbEvol`](@ref)

# 参考文献

  * Wikipedia: https://en.wikipedia.org/wiki/Ramsey_interferometry
