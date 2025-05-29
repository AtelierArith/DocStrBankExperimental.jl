```
MaxHourly(cols...) <: Function
```

この関数は、最大の集約された時間ごとの値を返します。指定されたidxsのすべての値をその時間に対して合計し、次に最大値を取ります。地域の負荷の最大値を知りたい場合など、負荷のような結果に適しています。

$$
\max_{y \in \text{yr\_idxs}, h \in \text{hr\_idxs}} \sum_{i \in \text{idxs}} \prod_{c \in \text{cols}} \text{table}[i, c][y, h]
$$
