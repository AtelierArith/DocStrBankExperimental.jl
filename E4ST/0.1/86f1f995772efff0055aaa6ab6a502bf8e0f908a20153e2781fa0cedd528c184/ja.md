```
MaxSingleLineHourly(cols...) <: Function
```

この関数は、InterfaceLimit Modificationのために特別に作成されており、最大単一ラインの電力フローを計算します。

$$
\max_{y \in \text{yr\_idxs}, h \in \text{hr\_idxs}} \sum_{i \in \text{idxs}} \prod_{c \in \text{cols}} \text{table}[i, c][y, h]
$$
