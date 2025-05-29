```
J = imsobel(I::GMTimage{<:UInt8, 2}; direction::Int=2)::GMTimage
```

ソベルエッジ検出フィルター。

グレースケールまたはバイナリ画像 I において、関数がエッジを見つけた場所に 1 を、その他の場所に 0 を含むバイナリ画像 BW を返します。

### 引数

  * `I::GMTimage`: 入力グレースケール画像。

### キーワード引数

  * `direction::Int=2`: 向きフラグ: `0` は水平エッジを検出、`1` は垂直エッジ、`2` はすべてのエッジを意味します。

### 戻り値

エッジ検出を行った新しい `GMTimage` グレースケール画像 `I`、エッジは明るくなります。

### 例

画像 "rice.png" の米粒をベクトル化してみましょう。画像のエッジにある粒は閉じておらず、したがって塗りつぶされていないため、結果は完璧ではありません。そして、それらは二重にポリゴン化され（内側と外側）、赤い線が太く見えます（しかし、実際にはそうではなく、単に二重になっています）。

```julia
I = gmtread(TESTSDIR * "assets/rice.png");
J = imsobel(I);
BW = binarize(J);
BW = bwskell(BW);	# 形状のより良い近似を得るためにスケルトン化します。
BW = imfill(BW);	# 粒の輪郭の外側と内側で「二重」ベクトル化を避けるために塗りつぶします。
D = polygonize(BW);
grdimage(I, figsize=5)
grdimage!(J, figsize=5, xshift=5.05)
grdimage!(BW, figsize=5, xshift=-5.05, yshift=-5.05)
grdimage!(I, figsize=5, xshift=5.05, plot=(data=D, lc=:red), show=true)
```
