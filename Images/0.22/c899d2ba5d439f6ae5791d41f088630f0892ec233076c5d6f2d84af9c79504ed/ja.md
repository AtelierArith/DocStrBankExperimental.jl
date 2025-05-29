```
thinned = thin_edges(img, gradientangle, [border])
thinned, subpix = thin_edges_subpix(img, gradientangle, [border])
thinned, subpix = thin_edges_nonmaxsup(img, gradientangle, [border]; [radius::Float64=1.35], [theta=pi/180])
thinned, subpix = thin_edges_nonmaxsup_subpix(img, gradientangle, [border]; [radius::Float64=1.35], [theta=pi/180])
```

2Dエッジ画像のエッジスリム。現在利用可能なアルゴリズムは非最大抑制のみで、エッジ画像とその勾配角を取り、各エッジポイントが勾配の方向で局所的な最大性を持つかどうかをチェックします。返される画像は、最大エッジの位置でのみ非ゼロです。

`border`は`padarray`で指定された境界条件のいずれかです。

最大エッジ画像に加えて、これらの関数の`_subpix`バージョンは、各局所最大のサブピクセル位置の推定値も2D配列または`Graphics.Point`オブジェクトの画像として返します。さらに、各局所最大はサブピクセル位置での推定値に調整されます。

現在、`_nonmaxsup`関数は最初の2つの関数呼び出しと同一ですが、追加のキーワード引数も受け入れます。`radius`は勾配の方向で検索する際に使用するステップサイズを示します。1.2から1.5の間の値が推奨されます（デフォルトは1.35）。`theta`は、`gradientangle`画像の角度を離散化する際に使用するステップサイズをラジアンで示します（デフォルト：1度のラジアン = pi/180）。

例:

```
g = rgb2gray(rgb_image)
gx, gy = imgradients(g)
mag, grad_angle = magnitude_phase(gx,gy)
mag[mag .< 0.5] = 0.0  # マグニチュード画像のしきい値
thinned, subpix =  thin_edges_subpix(mag, grad_angle)
```
