```
subject_selection_process(s::SG, target_signal::AbstractVector{T}, n_trials::I) where {SG<:Stimgen,T<:Real,I<:Integer}
```

合成被験者の意思決定プロセスを実行し、刺激生成メソッド `s` を使用してその場で刺激を生成します。
