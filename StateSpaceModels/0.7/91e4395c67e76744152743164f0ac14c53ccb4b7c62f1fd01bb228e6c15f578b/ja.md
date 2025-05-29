```
cross_validation(model::StateSpaceModel, steps_ahead::Int, start_idx::Int;
         n_scenarios::Int = 10_000,
         filter::KalmanFilter=default_filter(model),
         optimizer::Optimizer=default_optimizer(model)) where Fl
```

モデルの予測スキルを異なる期間と異なるリードタイムでベンチマークするために、ローリングウィンドウ推定と予測を行います。この関数は、リードタイムごとのMAEと平均CRPSを含む構造体を返します。モデルの予測の[クロスバリデーション](@ref)についての詳細を参照してください。

# 参考文献

  * DTUコース「31761 - 電力市場における再生可能エネルギー」YouTubeで視聴可能 https://www.youtube.com/watch?v=Ffo8XilZAZw&t=556s
