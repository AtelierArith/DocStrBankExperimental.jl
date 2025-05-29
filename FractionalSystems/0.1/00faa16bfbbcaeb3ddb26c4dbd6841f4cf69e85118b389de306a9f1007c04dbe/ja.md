```
fotf(numerator, order_of_numerator, denumerator, order_of_denumerator, delay)
```

分数次数システムにおける伝達関数を構築します。

### 例

```julia-repl
julia> G = fotf([1, 2], [0.3, 0.4], [1, 2], [0.5, 0.6], 2)
FOTF

s^{0.3} + 2s^{0.4}
------------------
s^{0.5} + 2s^{0.6}
```
