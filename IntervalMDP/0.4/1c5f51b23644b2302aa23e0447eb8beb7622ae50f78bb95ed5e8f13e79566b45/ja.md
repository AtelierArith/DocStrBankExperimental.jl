```
stateptr(mdp::MixtureIntervalMarkovDecisionProcess)
```

区間マルコフ決定過程の状態ポインタを返します。状態ポインタは整数のベクトルで、`i` 番目の要素は遷移確率行列における `i` 番目の状態の最初の要素のインデックスです。すなわち、`mixture_probs(transition_prob)[k][l][:, stateptr[j]:stateptr[j + 1] - 1]` は、モデル `k` および軸 `l` に対する（フラット化された）ソース状態 `j` の独立遷移確率行列であり、`mixture_probs(transition_prob)[:, stateptr[j]:stateptr[j + 1] - 1]` は `j` の重み行列です。
