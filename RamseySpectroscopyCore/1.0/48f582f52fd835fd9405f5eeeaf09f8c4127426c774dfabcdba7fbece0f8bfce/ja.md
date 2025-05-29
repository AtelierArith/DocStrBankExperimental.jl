```
rest!(self::StateVector, duration::FreeEvol) -> StateVector
```

外部の摂動がない場合に、システムの進化に従って量子システムの状態を変換します。

# 引数

  * `self` :   量子システムの現在の状態ベクトル。
  * `duration` :   量子システムの自由進化の時間。

# 戻り値

  * `StateVector` :   変換された `state` オブジェクトを持つ合成型インスタンス。

# 参照

  * [`StateVector`](@ref)
  * [`FreeEvol`](@ref)

# 参考文献

  * Wikipedia: https://en.wikipedia.org/wiki/Ramsey_interferometry
