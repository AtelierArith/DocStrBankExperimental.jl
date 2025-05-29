```
atomic_weight[elm::Element]::Union{NumberInterval, UncertainValue}
```

2020年の表に基づく原子量は https://ciaaw.org/atomic-weights.htm で確認できます。すべての元素が表されているわけではなく、すべての元素が名目上の同位体分布を持っているわけではありません。例えば、Tcのような元素は自然界には存在しません。他の元素、例えばPmのようなものは不安定です。ほとんどの原子量は `UncertainValue` インスタンスとして与えられていますが、一部は `NumberInterval` インスタンスとして与えられています。例えば、Pbの原子量は非常に変動が大きいため、範囲として示されています。（詳細についてはウェブサイトを参照してください。）
