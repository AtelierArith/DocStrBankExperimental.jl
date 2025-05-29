```
Sum(cols...) <: Function
```

結果の数式で使用される関数。idxs内の各インデックスに対して列の積の合計を計算します。

$$
\sum_{i \in \text{idxs}} \prod_{c \in \text{cols}} \text{table}[i, c]
$$
