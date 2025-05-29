```
stateptr(mdp::OrthogonalIntervalMarkovDecisionProcess)
```

区間マルコフ決定過程の状態ポインタを返します。状態ポインタは整数のベクトルで、`i` 番目の要素は遷移確率行列における `i` 番目の状態の最初の要素のインデックスです。すなわち、`transition_prob[l][:, stateptr[j]:stateptr[j + 1] - 1]` は、軸 `l` に対する（フラット化された）ソース状態 `j` の遷移確率行列です。
