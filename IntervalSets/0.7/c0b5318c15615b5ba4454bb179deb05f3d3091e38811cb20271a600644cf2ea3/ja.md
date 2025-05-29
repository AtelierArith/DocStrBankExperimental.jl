`Interval{L,R}(left, right)` は、L,R が :open または :closed の場合、次の条件を満たす `x` を含む区間集合です。

1. `left ≤ x ≤ right` もし `L == R == :closed` の場合
2. `left < x ≤ right` もし `L == :open` かつ `R == :closed` の場合
3. `left ≤ x < right` もし `L == :closed` かつ `R == :open` の場合、または
4. `left < x < right` もし `L == R == :open` の場合
