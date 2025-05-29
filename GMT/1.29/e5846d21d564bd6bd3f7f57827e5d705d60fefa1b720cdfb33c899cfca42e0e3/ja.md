```
J = bwhitmiss(I::Union{GMTimage{<:UInt8, 2}, GMTimage{<:Bool, 2}}, interval::Matrix{<:Integer})::GMTimage
```

バイナリ画像に対してヒットミス操作を行います。この操作は*interval*と呼ばれる行列によって定義されます。

*interval*は、要素が0または1または2の行列で、2つの構造要素SE1とSE2を*結合*することによって得られます。0は無視されます。1はSE1のドメインを構成し、2はSE2のドメインを構成します。

### 引数

  * `I::Union{GMTimage{<:UInt8, 2}, GMTimage{<:Bool, 2}}`: 入力画像。

### キーワード引数

  * `hsize::Int=3`: 'ボックス'構造要素の水平サイズ。
  * `vsize::Int=3`: 'ボックス'構造要素の垂直サイズ。
  * `smooth::Int=0`: 畳み込みスムージングフィルタの半幅。幅は(2 * smoothing + 1)で、0は何もしないことを意味します。

### 戻り値

ヒットミスが適用された、`I`と同じ型の新しい`GMTimage`。

### 例（DIP本から）

bw画像のオブジェクトの左上隅のピクセルを特定するタスクを考えます。東と南の隣接ピクセル（これらは'ヒット'）を持ち、北東、西北、西または南西の隣接ピクセル（これらは'ミス'）を持たない前景ピクセルを特定したいと考えています。これらの要件は、次のようなinterval行列を導きます：

```julia
interval = [2 2 2; 2 1 1; 2 1 0];
I = gmtread(TESTSDIR * "assets/small_squares.png");
J = bwhitmiss(I, interval);
grdimage(I, figsize=6)
grdimage!(J, figsize=6, xshift=6.05, show=true)
```
