```
t_from_arclength(arc_len::Float64, e::Ellipse)
```

与えられた弧長 `arc_len` に基づいて、回転していない楕円上の位置の角度 t（0 から 2π ラジアンの間）を計算します。これは、楕円の周囲に沿って正の主軸から反時計回りに測定されます。楕円の x 軸は主軸です。この関数を呼び出すのではなく、[`t_from_arclength_general(arc_len::T, a::T, b::T) where T<:Float64`] を呼び出すことをお勧めします。これは、楕円の主軸が y 軸である場合のケースを処理します。

ジョン・D・クックによる Python 関数 `t_from_length` の Julia バージョンです。[John D. Cook](https://www.johndcook.com/blog/2022/11/02/ellipse-rng/)。

# 引数

  * `arc_len`: 弧長、0.0 と楕円の周囲の間、正の主軸から反時計回りに楕円の周囲に沿って測定されます。
  * `e`: 楕円を定義する有効な [`EllipseSampling.Ellipse`](@ref) 構造体。
