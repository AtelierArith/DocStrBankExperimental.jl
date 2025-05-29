```
PrimeIdealsSet(O::AbsSimpleNumFieldOrder, f, t; proof = false,
                               indexdivisors = true,
                               ramified = true,
                               degreebound = degree(O),
                               coprimeto = false)
```

$$
S
$$

を返します。これは、$f \leq \min(\mathfrak p) \leq t$を満たす$\mathcal O$の素イデアル$\mathfrak p$を表す反復可能なオブジェクトです。

オプションの引数は、指数除数を除外したり、分岐した素イデアルを除外したり、`degreebound`以下の次数を持ち、`coprimeto`と互いに素な素イデアルのみを含めるために使用できます。

$$
t=-1
$$

の場合、上限は無限大です。

`coprimeto`が指定されている場合、それは整数、$\mathcal O$の要素、または$\mathcal O$の非ゼロイデアルでなければなりません。
