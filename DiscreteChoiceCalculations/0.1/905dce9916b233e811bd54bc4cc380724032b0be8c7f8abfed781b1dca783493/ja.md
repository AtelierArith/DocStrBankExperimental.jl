```julia
ECV_and_probabilities(noise, V)

```

IIDランダム変数 $εᵢ ∼ 	ex{noise}$ に対して、次を返します。

1. *期待継続価値 (ECV)* `ECV = E[maxᵢ (Vᵢ + εᵢ)]``, および
2. $$
    X = Vᵢ + εᵢ
    $$

    の確率 $πᵢ$

を `NamedTuple{(:ECV,:π)}` として、ここで `π` は `V` と同じ「形」を持ち、他の特性は可能な限り保持されます（例えば `SArray`s、`Tuple`s などは類似の型にマッピングされます）。
