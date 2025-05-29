```
struct OneDAdvectingFlow <: AbstractAdvectingFlow
```

一次元の `TracerAdvectionDiffusion.Problem` の輸送流のコンテナ。含まれるもの：

  * `u::Function`: 輸送流の $x$ 成分のための関数
  * `steadyflow::Bool`: 流れが定常であるかどうかを示すブール値（すなわち、時間依存でない）
