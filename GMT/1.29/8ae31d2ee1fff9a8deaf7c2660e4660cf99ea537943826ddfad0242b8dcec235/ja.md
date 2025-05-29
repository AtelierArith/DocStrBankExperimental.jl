```
J = immorphgrad(I::Union{GMTimage{<:UInt8, 2}, GMTimage{<:Bool, 2}}; hsize=3, vsize=3, smooth=0)::GMTimage
```

グレースケールまたはバイナリ画像の形態学的勾配を計算します。

これは、画像の膨張と収縮の違いです。パラメータ `smooth` を使用して結果を平滑化できます。

### 引数

  * `I::Union{GMTimage{<:UInt8, 2}, GMTimage{<:Bool, 2}}`: 入力画像。

### キーワード引数

  * `hsize::Int=3`: 'ボックス' 構造要素の水平方向のサイズ。
  * `vsize::Int=3`: 'ボックス' 構造要素の垂直方向のサイズ。
  * `smooth::Int=0`: 畳み込み平滑化フィルタの半幅。幅は (2 * smoothing + 1) であり、0 は何もしないことを意味します。

### 戻り値

形態学的勾配が適用された、`I` と同じタイプの新しい `GMTimage`。

### 例

結果はオブジェクトの輪郭のように見えます。

```julia
I = gmtread(TESTSDIR * "assets/j.png");
J = immorphgrad(I, hsize=5, vsize=5);
grdimage(I, figsize=5)
grdimage!(J, figsize=5, xshift=5, show=true)
```
