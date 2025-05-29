```
evaluate_motion!(motion::ILMMotion,x::AbstractVector,t::Real)
```

現在の関節状態ベクトル `x` と時間 `t` に基づいて、`motion` 内のボディ変換と速度を更新します。
