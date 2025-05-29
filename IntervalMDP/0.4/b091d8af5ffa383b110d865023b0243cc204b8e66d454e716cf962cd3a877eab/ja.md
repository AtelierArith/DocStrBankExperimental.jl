```
IntervalMarkovChain(transition_prob::IntervalProbabilities, initial_states::InitialStates = AllStates())
```

区間遷移確率の正方行列ペアから区間マルコフ連鎖を構築します。初期状態はオプションであり、指定されていない場合はすべての状態が初期状態であると見なされます。状態の数は遷移確率行列のサイズから推測されます。

返される型は、各状態に対して1つのアクションのみを持つ`IntervalMarkovDecisionProcess`です（すなわち、すべての`j`に対して`stateptr[j + 1] - stateptr[j] == 1`）。これは、価値反復のインターフェースを統一するために行われます。
