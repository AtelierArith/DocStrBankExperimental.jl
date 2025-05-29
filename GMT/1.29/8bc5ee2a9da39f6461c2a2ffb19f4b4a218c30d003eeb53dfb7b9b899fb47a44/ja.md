```
J = imrankfilter(I::GMTimage; width::Int=3, height::Int=0, rank=0.5)::GMTimage
```

ランク順フィルタ。

これは、各ピクセルに対して、ピクセルの「中心」に配置された長方形で与えられるピクセルの近傍を定義します。この $width x height$ ピクセルのセットは値の分布を持ち、昇順にソートされると、rank*(wf*hf-1) ピクセルがより低いか等しい値を持ち、(1-rank)*(wf*hf-1) ピクセルが等しいかそれ以上の値を持つようなピクセルを選択します。言い換えれば、`rank=0` は最小値を返し、`rank=1` はボックス内の最大値を返し、`rank=0.5` は中央値を返します。他の値は分位数を返します。

### 引数

  * `I::GMTimage`: 入力画像。これはRGB、グレースケール、またはバイナリ画像である可能性があります。

### キーワード引数

  * `width::Int=3`: フィルタの幅。
  * `height::Int`: フィルタの高さ（デフォルトは `width`）。
  * `rank=0.5`: ランク。

### 戻り値

フィルタ処理された画像を持つ、`I` と同じタイプの新しい `GMTimage`。

### 例

```julia
I = gmtread(TESTSDIR * "assets/small_squares.png");
J = imrankfilter(I, width=10);
grdimage(I, figsize=6)
grdimage!(J, figsize=6, xshift=6, show=true)
```
