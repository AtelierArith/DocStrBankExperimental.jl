```
reward(m::POMDP, s, a)
reward(m::MDP, s, a)
```

s-aペアに対する即時報酬を返します。

```
reward(m::POMDP, s, a, sp)
reward(m::MDP, s, a, sp)
```

s-a-s'トリプルに対する即時報酬を返します。

```
reward(m::POMDP, s, a, sp, o)
```

s-a-s'-o四元組に対する即時報酬を返します。

いくつかの問題では、`reward(m, s, a, sp)`や`reward(m, s, a, sp, o)`を表現する方が、`reward(m, s, a)`を表現するよりも簡単です。しかし、SARSOPなどの一部のソルバーは、`reward(m, s, a)`のみを使用できます。両方を問題に対して実装することは可能ですが、`reward(m, s, a)`が実装されている場合、それは`reward(m, s, a, sp[, o])`と一貫性があるべきです。つまり、すべての遷移先状態と観測に対する期待値であるべきです。
