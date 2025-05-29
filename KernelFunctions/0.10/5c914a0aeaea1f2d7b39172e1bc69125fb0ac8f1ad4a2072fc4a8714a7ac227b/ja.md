```
NormalizedKernel(k::Kernel)
```

`k`から派生した正規化カーネルです。

# 定義

入力 $x, x'$ に対して、カーネル $k$ から派生した正規化カーネル $\widetilde{k}$ は次のように定義されます。

$$
\widetilde{k}(x, x'; k) = \frac{k(x, x')}{\sqrt{k(x, x) k(x', x')}}.
$$
