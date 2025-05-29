```
PyArray{T,N,M,L,R}(x; copy=true, array=true, buffer=true)
```

Python配列`x`をJuliaの`AbstractArray{T,N}`としてラップします。

入力`x`は`bytes`、`bytearray`、`array.array`、`numpy.ndarray`、またはバッファプロトコルを満たす任意のものであるか（`buffer=true`の場合）、またはnumpy配列インターフェースを満たすものである必要があります（`array=true`の場合）。

`copy=false`の場合、結果の配列は`x`内のデータを直接ラップすることが保証されます。`copy=true`の場合、配列を生成するために必要に応じてコピーが行われます。

型パラメータはすべてオプションであり、次のようになります：

  * `T`: 要素の型。
  * `N`: 次元の数。
  * `M`: 配列が可変である場合は真。
  * `L`: 配列が高速な線形インデックスをサポートする場合は真。
  * `R`: 基本バッファの要素型。しばしば`T`と等しい。
