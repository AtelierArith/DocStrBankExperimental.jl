```
EpsilonGreedyPolicy(domain, policy, epsilon, [rng::AbstractRNG])
```

`epsilon`の確率で均等にランダムに行動し、それ以外の場合は基礎となる`policy`に従って最良の行動を選択するポリシーです。最良の行動が複数ある場合、タイブレークはランダムに行われます。各状態で利用可能な行動を決定するために`domain`を提供する必要があります。
