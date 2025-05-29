```
&(s1,s2)
s1 & s2
```

二つの[`StoppingCriterion`](@ref)を[`StopWhenAll`](@ref)内で組み合わせます。もし`s1`（または`s2`）がすでに[`StopWhenAll`](@ref)である場合、`s2`（または`s1`）は`s1`（または`s2`）内の[`StoppingCriterion`](@ref)のリストに追加されます。

# 例

```
a = StopAfterIteration(200) & StopWhenChangeLess(M, 1e-6)
b = a & StopWhenGradientNormLess(1e-6)
```

は次のように同じです。

```
a = StopWhenAll(StopAfterIteration(200), StopWhenChangeLess(M, 1e-6))
b = StopWhenAll(StopAfterIteration(200), StopWhenChangeLess(M, 1e-6), StopWhenGradientNormLess(1e-6))
```
