```
fht(A [, dims])
```

配列 `A` の多次元ファストハートレー変換 (FHT) を実行します。オプションの `dims` 引数は、変換する次元の iterable サブセット（整数、範囲、タプル、または配列など）を指定します。変換された次元に沿った `A` のサイズが小さな素数の積である場合、最も効率的です。`Base.nextprod` を参照してください。さらに効率を高めるために [`plan_fht()`](@ref) も参照してください。

一次元 FHT は、次のように定義される一次元離散ハートレー変換 (DHT) を計算します。

$$
\operatorname{DFT}(A)[k] = \sum_{n=1}^{\operatorname{length}(A)} \operatorname{cas} \left( +i\frac{2\pi(n-1)(k-1)}{\operatorname{length}(A)} \right) A[n],
$$

ここで、$\operatorname{cas}$ はコサインとサインの関数、またはハートレーカーネルと呼ばれるもので、次のように定義されます。

$$
\operatorname{cas}(x) = \cos(x) + \sin(x).
$$

多次元 FHT は、単に `A` の各変換次元に沿ってこの操作を実行します。
