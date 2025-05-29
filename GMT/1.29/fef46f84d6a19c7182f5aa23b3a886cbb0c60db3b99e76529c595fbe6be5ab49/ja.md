```
J = bwperim(I::Union{GMTimage{<:UInt8, 2}, GMTimage{<:Bool, 2}}; hsize=3, vsize=3, sel=nothing)::GMTimage
```

バイナリ画像 I のオブジェクトの周囲を見つけます。

ピクセルは、非ゼロであり、少なくとも1つのゼロ値ピクセルに接続されている場合、周囲の一部と見なされます。画像の周囲を検出するには、構造要素はサイズ `3 x 3` のボックスであるべきですが（または、デフォルトを使用する方が良い）、異なるサイズを指定することもできます。この操作は、`I` の侵食を `I` から引くことから成り立ち、形態学的 `内部勾配` とも呼ばれます。

### 引数

  * `I::Union{GMTimage{<:UInt8, 2}, GMTimage{<:Bool, 2}}`: 入力画像。

### キーワード引数

  * `hsize::Int=3`: 'ボックス' 構造要素の水平サイズ。
  * `vsize::Int=3`: 'ボックス' 構造要素の垂直サイズ。
  * `sel=nothing`: 構造要素（$strel$ 関数を参照）。`hsize` および `vsize` オプションの代替。$nothing$ に等しい場合、サイズ `hsize` x `vsize` の構造ボックスが使用されます。

### 戻り値

周囲を持つ `I` と同じタイプの新しい `GMTimage`。

### 例

```julia
I = gmtread(TESTSDIR * "assets/circles.png");
J = bwperim(I);
grdimage(I, figsize=6)
grdimage!(J, figsize=6, xshift=6, show=true)
```
