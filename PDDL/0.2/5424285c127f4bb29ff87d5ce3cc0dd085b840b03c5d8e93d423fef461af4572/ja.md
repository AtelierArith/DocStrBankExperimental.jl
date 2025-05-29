```
evaluate(domain::Domain, state::State, term::Term)
```

与えられた `domain` と `state` において、基盤となる `term` を評価します。`term` が数値的な流動を参照する場合、その流動の値が返されます。論理的な述語に対しては、`evaluate` は `satisfy` と同等です。
