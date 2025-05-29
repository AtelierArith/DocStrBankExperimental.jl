```
gausslaguerre(n::Integer, α::Real) -> x, w  # ノード、重み
```

一般化された[ガウス・ラグランジュ数値積分](https://en.wikipedia.org/wiki/Gauss%E2%80%93Laguerre_quadrature)のノード `x` と重み `w` を返します。

$$
\int_{0}^{+\infty} f(x) x^\alpha e^{-x} dx \approx \sum_{i=1}^{n} w_i f(x_i)
$$

# 例

```jldoctest
julia> x, w = gausslaguerre(3, 1.0);

julia> f(x) = x^4;

julia> I = dot(w, f.(x));

julia> I ≈ 120
true
```

オプションで、縮小された数値積分ルールを計算することができます。その場合、浮動小数点精度型で重みがアンダーフローしない点と重みのみが計算されます。オプション引数 `reduced = true` を指定してください。

コードは一般的ですが、アルゴリズムの選択に関するヒューリスティックな選択は、`Float64` 型に対してのみ機械精度の精度を達成することに基づいています。デフォルトのアルゴリズムの選択が望ましい精度を達成しない場合、ユーザーは以下のルーチンを手動で呼び出すことができます：

  * `gausslaguerre_GW`: ゴルブ・ウェルシュに基づく計算
  * `gausslaguerre_rec`: 再帰関係を使用した評価に適用されるニュートン反復に基づく計算
  * `gausslaguerre_asy`: 漸近展開

```
