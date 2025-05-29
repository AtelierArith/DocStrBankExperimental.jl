```
run_filter(filter::AbstractFilter, b0::GaussianBelief, action_history::Vector{AbstractVector},
        measurement_history::Vector{AbstractVector})
```

初期信念 b0、アクションと測定の履歴のための同じサイズの配列、およびフィルタを考慮して、フィルタを使用して信念を更新し、すべての信念のベクトルを返します。
