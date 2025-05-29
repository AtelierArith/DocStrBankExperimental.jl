```
set_inactive(sc::SpeedController, inactive::Bool)
```

スピードコントローラーを非アクティブにするには、パラメータinactiveがtrueの場合、そうでなければアクティブにし、インテグレーターとリミッターをリセットします。

## パラメータ

  * sc::[SpeedController](@ref): 非アクティブまたはアクティブにするスピードコントローラー

## 戻り値

  * 何も返さない
