```
mapwindow(f, img, window; [border="replicate"], [indices=axes(img)]) -> imgf
```

`img`のスライディングウィンドウに`f`を適用します。ウィンドウのサイズまたは軸は`window`で指定します。例えば、`mapwindow(median!, img, window)`は、`img`に似た値の`Array`を返します（もちろん中央値フィルタリングされたものです）。一方、`mapwindow(extrema, img, window)`は、`img`の各点を中心としたサイズ`window`のウィンドウに対する`(min,max)`タプルの`Array`を返します。

関数`f`は、現在の点を囲むデータのウィンドウのバッファ`buf`を受け取ります。`window`がDimsタプル（整数のタプル）として指定されている場合、すべての整数は奇数でなければならず、ウィンドウは現在の画像点の周りに中心を置きます。例えば、`window=(3,3)`の場合、`f`は`imgf[i,j]`からのオフセット`(-1:1, -1:1)`に対応するArray `buf`を受け取ります。あるいは、`window`はAbstractUnitRangesのタプルであり、その場合、指定された範囲が`buf`に使用されます。これにより、必要に応じて非対称ウィンドウを使用することができます。

`border`は`img`のエッジがどのように処理されるべきかを指定します。詳細は`imfilter`を参照してください。

最後に、`indices`は不要な計算を省略することを可能にします。これは、サブイメージやmapwindowのストライドバリアントのようなことを行いたい場合に便利です。動作は次のようになります：

```julia
mapwindow(f, img, window, indices=(2:5, 1:2:7)) == mapwindow(f,img,window)[2:5, 1:2:7]
```

未使用の値の計算を省略するため、より効率的に動作します。

`f`が受け取るバッファ`buf`のデータは`img`からコピーされ、バッファのメモリは再利用されるため、`f`は`buf`への参照を返さないようにする必要があります。これ

```julia
f = buf->copy(buf) # f = buf->bufではなく
mapwindow(f, img, window, indices=(2:5, 1:2:7))
```

は期待通りに動作します。

`AbstractVector`入力のみを受け取る関数の場合、最初に`default_shape`を特化させる必要があるかもしれません：

```julia
f = v->quantile(v, 0.75)
ImageFiltering.MapWindow.default_shape(::typeof(f)) = vec
```

その後、`mapwindow(f, img, (m,n))`は75パーセンタイルでフィルタリングされるはずです。

参照：[`imfilter`](@ref)もご覧ください。
