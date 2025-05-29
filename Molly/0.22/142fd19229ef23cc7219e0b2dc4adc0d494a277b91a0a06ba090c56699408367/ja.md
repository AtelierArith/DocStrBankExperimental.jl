```
virial(sys, neighbors=find_neighbors(sys), step_n=0; n_threads=Threads.nthreads())
virial(inter, sys, neighbors, step_n; n_threads=Threads.nthreads())
```

システムのビリアルまたは一般的な相互作用からのビリアルを計算します。

ビリアルは次のように定義されます。

$$
\Xi = -\frac{1}{2} \sum_{i,j>i} r_{ij} \cdot F_{ij}
$$

カスタム一般相互作用タイプはこの関数を実装できます。

これは、ペアワイズ相互作用のみを含むシステム、または特定の相互作用、制約、および[`virial`](@ref)が定義されていない一般相互作用がビリアルに寄与しない場合にのみ使用する必要があります。
