```
getmatrix()
```

現在のワークスペース（位置、スケール、方向）を6要素のベクトルとして取得します：

```julia
[xx, yx, xy, yy, x0, y0]
```

  * `xx` アフィン変換の成分
  * `yx` アフィン変換の成分
  * `xy` アフィン変換の成分
  * `yy` アフィン変換の成分
  * `x0` アフィン変換の平行移動成分
  * `y0` アフィン変換の平行移動成分

描画が最初に作成されると、'matrix' は次のようになります：

```
getmatrix() = [1.0, 0.0, 0.0, 1.0, 0.0, 0.0]
```

原点が400/400に移動すると、次のようになります：

```
getmatrix() = [1.0, 0.0, 0.0, 1.0, 400.0, 400.0]
```

'matrix' を元に戻すには：

```
setmatrix([1.0, 0.0, 0.0, 1.0, 0.0, 0.0])
```

現在の 'matrix' を6要素の 'matrix' `a` で乗算して変更するには、`transform(a::Array)` を参照してください。

Luxor/Cairo 'matrix' 形式（6要素の Vector{Float64}）と3x3のJulia行列の間で変換するには、`cairotojuliamatrix(c)` と `juliatocairomatrix(c)` を使用します。

また、`rotationmatrix(a)`、`translationmatrix()`、および `scalingmatrix()` も参照してください。

# 拡張ヘルプ

以下は基本的な行列変換のいくつかです：

  * 平行移動

    `transform([1, 0, 0, 1, dx, dy])` は `dx`、`dy` だけシフトします
  * スケーリング

    `transform([fx 0 0 fy 0 0])` は `fx` と `fy` でスケールします
  * 回転

    `transform([cos(a), -sin(a), sin(a), cos(a), 0, 0])` は `a` ラジアンだけ回転します

    Oの周りに回転: [c -s s c 0 0]
  * シアー

    `transform([1 0 a 1 0 0])` はx方向に `a` だけシアーします

    y方向に `a` だけシアー: `[1 a 0 1 0 0]`
  * x方向のスキュー

    `transform([1, 0, tan(a), 1, 0, 0])` はx方向に `a` だけスキューします
  * y方向のスキュー

    `transform([1, tan(a), 0, 1, 0, 0])` はy方向に `a` だけスキューします
  * 反転

    `transform([fx, 0, 0, fy, centerx * (1 - fx), centery * (fy-1)])` は `centerx`/`centery` を中心に反転します
  * 反射

    `transform([1 0 0 -1 0 0])` はx軸で反射します

    `transform([-1 0 0 1 0 0])` はy軸で反射します
