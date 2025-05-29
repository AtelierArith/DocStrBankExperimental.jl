```
overapproximate(P::VPolygon, ::Type{<:LinearMap{N,<:Hyperrectangle}}) where {N}
```

最小面積の回転矩形で凸多角形を過大評価します。

### 入力

  * `P` – 凸多角形
  * `LinearMap{N,<:Hyperrectangle}` – 目標タイプ

### 出力

`Hyperrectangle`の`LinearMap`。

### アルゴリズム

このメソッドは、[この投稿](https://gis.stackexchange.com/a/22934)で説明されているアプローチに従っており、それ自体は[この投稿](https://gis.stackexchange.com/a/22904)に基づいています。

一般的に、回転矩形は多角形と少なくとも1つの辺を共有しなければなりません。したがって、有限個の矩形を試すだけで十分です。線形代数のいくつかのトリックを使用すると、対応する回転と矩形を優雅に構築できます。
