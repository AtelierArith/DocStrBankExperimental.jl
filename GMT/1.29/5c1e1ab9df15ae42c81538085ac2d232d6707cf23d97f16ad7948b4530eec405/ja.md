```
J = imerode(I::Union{GMTimage{<:UInt8, 2}, GMTimage{<:Bool, 2}}; hsize=3, vsize=3, sel=nothing)::GMTimage
```

グレースケールまたはバイナリ画像Iを侵食します。

侵食は、幅`hsize`と高さ`vsize`の0と1の行列を使用して行われるか、可能であれば構造要素`sel`を使用して行われます。後者のケースは高速ですが、バイナリ画像のみに利用可能であり、ここでの*バイナリ*画像とは、ブール画像またはUInt8型の0と1のみを含む画像を指します。

### 引数

  * `I::Union{GMTimage{<:UInt8, 2}, GMTimage{<:Bool, 2}}`: 入力画像。

### キーワード引数

  * `hsize::Int=3`: 'ボックス'構造要素の水平サイズ。
  * `vsize::Int=3`: 'ボックス'構造要素の垂直サイズ。
  * `sel=nothing`: 構造要素（$strel$関数を参照）。`hsize`および`vsize`オプションの代替。$nothing$と等しい場合、サイズ`hsize` x `vsize`の構造ボックスが使用されます。

### 戻り値

侵食が適用された、`I`と同じ型の新しい`GMTimage`。

### 例

半径10、5、20のディスクによる侵食

```julia
I = gmtread(TESTSDIR * "assets/chip.png");
J1 = imerode(I, sel=strel("disk", 10));
J2 = imerode(I, sel=strel("disk", 5));
J3 = imerode(I, sel=strel("disk", 20));
grdimage(I, figsize=6)
grdimage!(J1, figsize=6, xshift=6.1)
grdimage!(J2, figsize=6, xshift=-6.1, yshift=-6.1)
grdimage!(J3, figsize=6, xshift=-6.1, show=true)
```
