```
propagate!(state[s], model::HiddenStateModel[, dt])
```

モデルに従って状態を伝播させます。`ContinuousTime`モデルの場合、時間ステップ`dt`を提供する必要があります。複数の状態は、列が状態に対応する行列として与えられ、独立同分布で処理されます。
