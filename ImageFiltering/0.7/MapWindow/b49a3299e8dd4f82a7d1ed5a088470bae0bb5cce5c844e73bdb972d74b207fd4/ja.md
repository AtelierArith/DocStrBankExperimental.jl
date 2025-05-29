```
mapwindow(f::F, img, window; 
    border = "replicate",
    indices = default_imginds(img, window, border), callmode=:copy!)
```

`f`を`img`のスライディングウィンドウに適用し、ウィンドウサイズまたは軸は`window`で指定します。例えば、`mapwindow(median!, img, window)`は`img`に似た値の配列を返します（もちろん中央値フィルタリングされたものです）。一方、`mapwindow(extrema, img, window)`は、`img`の各点を中心にしたウィンドウサイズ`window`の(min, max)タプルの配列を返します。

関数`f`は、現在の点を囲むデータのウィンドウのためのバッファ`buf`を受け取ります。

`window`がDimsタプル（整数のタプル）として指定されている場合、すべての整数は奇数でなければならず、ウィンドウは現在の画像点の周りに中心を置きます。

例えば、`window = (3,3)`の場合、`f`は`imgf[i, j]`からのオフセット(-1:1, -1:1)に対応する配列`buf`を受け取ります。この計算が現在行われている点のために。あるいは、`window`は`AbstractUnitRange`のタプルであることもでき、その場合、指定された範囲が`buf`に使用されます。これにより、必要に応じて非対称ウィンドウを使用することができます。

## サブイメージへの制限

`indices`キーワードを使用すると、`mapwindow`をサブイメージで行う場合や、`mapwindow`のストライドバリアントを行う場合に、不要な計算を省略できます。

この呼び出し：

```julia
mapwindow(f, img, window, indices=(2:5, 1:2:7))
```

は、同等のものよりも効率的です：

```julia
mapwindow(f, img, window)[2:5, 1:2:7]
```

なぜなら、未使用の値の計算を省略するからです。

`f`が受け取るバッファ`buf`のデータは`img`からコピーされ、バッファのメモリは再利用されるため、`f`は`buf`への参照を返すべきではありません。

このコード：

```julia
f = buf -> copy(buf) # f = buf -> bufではなく
mapwindow(f, img, window, indices=(2:5, 1:2:7))
```

は期待通りに動作します。

`AbstractVector`入力のみを受け取る関数の場合、最初に`default_shape`を特化させる必要があるかもしれません：

```julia
f = v -> quantile(v, 0.75)
ImageFiltering.MapWindow.default_shape(::typeof(f)) = vec
```

その後、`mapwindow(f, img, (m, n))`は75パーセンタイルでフィルタリングされるはずです。

参照： [`imfilter`](@ref).
