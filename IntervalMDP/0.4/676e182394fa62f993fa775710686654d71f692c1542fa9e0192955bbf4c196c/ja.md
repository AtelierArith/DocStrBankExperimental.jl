```
MixtureIntervalMarkovChain(transition_prob::MixtureIntervalProbabilities, initial_states::InitialStates = AllStates())
```

混合区間マルコフ連鎖を混合区間遷移確率から構築します。初期状態はオプションであり、指定されていない場合はすべての状態が初期状態と見なされます。状態の数は遷移確率行列のサイズから推測されます。

返される型は、各状態に対して1つのアクションのみを持つ`MixtureIntervalMarkovDecisionProcess`です（すなわち、すべての`j`に対して`stateptr[j + 1] - stateptr[j] == 1`）。これは、価値反復のインターフェースを統一するために行われます。
