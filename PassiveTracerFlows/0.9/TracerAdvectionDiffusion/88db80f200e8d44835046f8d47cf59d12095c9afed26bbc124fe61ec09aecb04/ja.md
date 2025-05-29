```
struct TwoDAdvectingFlow <: AbstractAdvectingFlow
```

二次元 `TracerAdvectionDiffusion.Problem` の輸送流のコンテナ。含まれるもの：

  * `u::Function`: 輸送流の $x$ 成分の関数
  * `v::Function`: 輸送流の $y$ 成分の関数
  * `steadyflow::Bool`: 流れが定常であるかどうかを示すブール値（すなわち、時間依存でない）
