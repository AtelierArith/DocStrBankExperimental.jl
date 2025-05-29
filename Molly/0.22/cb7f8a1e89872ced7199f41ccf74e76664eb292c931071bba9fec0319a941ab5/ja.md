```
pressure(sys, neighbors=find_neighbors(sys), step_n=0; n_threads=Threads.nthreads())
```

システムの圧力を計算します。

圧力は次のように定義されます。

$$
P = \frac{1}{V} \left( NkT - \frac{2}{D} \Xi \right)
$$

ここで `V` はシステムの体積、`N` は原子の数、`k` はボルツマン定数、`T` はシステムの温度、`D` は次元の数、`Ξ` は [`virial`](@ref) を使用して計算されたビリアルです。

これは、対相互作用のみを含むシステム、または特定の相互作用、制約、一般的な相互作用が [`virial`](@ref) を定義せずにビリアルに寄与しない場合にのみ使用するべきです。無限境界とは互換性がありません。
