```
actions(m::Union{MDP,POMDP})
```

(PO)MDPの全アクション空間を返します。

---

```
actions(m::Union{MDP,POMDP}, s)
```

状態`s`から取ることができるアクションを返します。

---

```
actions(m::POMDP, b)
```

信念`b`から取ることができるアクションを返します。

観察依存のアクション空間を実装するには、`actions(m, b)`の実装内で信念`b`に関連付けられた観察を取得するために`currentobs(b)`を使用してください。
