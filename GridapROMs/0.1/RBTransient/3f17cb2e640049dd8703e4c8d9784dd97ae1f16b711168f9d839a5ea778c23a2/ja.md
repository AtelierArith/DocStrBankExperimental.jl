```
struct TransientProjection <: Projection
  projection_space::Projection
  projection_time::Projection
end
```

一時的な問題のための射影演算子で、空間射影と時間射影を含みます。時空間射影演算子は次のように等しいです。

`projection_time ⊗ projection_space`

これは効率の理由から、明示的には計算されません。
