```
NystromFact
```

Nystrom因子分解を格納するための型。この因子分解は、次の2つのフィールドを含みます：`W` と `C`。これらは次の条件を満たす2つの行列です：

$$
\mathbf{K} \approx \mathbf{C}^{\intercal}\mathbf{W}\mathbf{C}
$$
