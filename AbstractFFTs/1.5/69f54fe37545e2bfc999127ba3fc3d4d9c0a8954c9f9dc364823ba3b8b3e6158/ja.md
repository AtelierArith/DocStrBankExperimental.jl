```
fft(A [, dims])
```

配列 `A` の多次元FFTを実行します。オプションの `dims` 引数は、変換する次元の iterable サブセット（整数、範囲、タプル、または配列など）を指定します。変換された次元に沿った `A` のサイズが小さな素数の積である場合、最も効率的です。`Base.nextprod` を参照してください。さらに効率を高めるために [`plan_fft()`](@ref) も参照してください。

一次元FFTは、次のように定義される一次元離散フーリエ変換（DFT）を計算します。

$$
\operatorname{DFT}(A)[k] =
  \sum_{n=1}^{\operatorname{length}(A)}
  \exp\left(-i\frac{2\pi
  (n-1)(k-1)}{\operatorname{length}(A)} \right) A[n].
$$

多次元FFTは、単に `A` の各変換次元に沿ってこの操作を実行します。

!!! note
    これはデフォルトで多次元FFTを実行します。他の言語（PythonやOctaveなど）のFFTライブラリは、配列の最初の非単一次元に沿って一次元FFTを実行します。比較を行う際に注意が必要です。

