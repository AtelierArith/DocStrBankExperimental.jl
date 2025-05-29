```
modify(f, A::AbstractDimArray) => AbstractDimArray
modify(f, s::AbstractDimStack) => AbstractDimStack
modify(f, dim::Dimension) => Dimension
modify(f, x, lookupdim::Dimension) => typeof(x)
```

親データを変更し、オブジェクトラッパーを変更せずに再構築します。`f`は元のサイズと同じ`AbstractArray`を返す必要があります。

このメソッドは、オブジェクトの親配列タイプを入れ替える方法として主に便利です。

## 例

以前に定義された`DimArray`がある場合、次のようにしてNvidia GPUにコピーできます。

```julia
A = DimArray(rand(100, 100), (X, Y))
modify(CuArray, A)
```

これは`DimStack`内のすべてのデータレイヤーにも適用されます。
