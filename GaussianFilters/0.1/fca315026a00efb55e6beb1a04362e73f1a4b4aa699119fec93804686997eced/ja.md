```
belief_ellipse(b::GaussianBelief, P::Float=0.95; δ::Number=5)
```

2Dガウス信念のxおよびyポイントを構築して返します。Pは楕円によって捕捉される総確率（P ∈ (0,1)）であり、δはポイント間の度数の増分です。
