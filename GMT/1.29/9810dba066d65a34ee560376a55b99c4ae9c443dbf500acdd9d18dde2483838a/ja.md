```
J = imopen(I::Union{GMTimage{<:UInt8, 2}, GMTimage{<:Bool, 2}}; hsize=3, vsize=3, sel=nothing)::GMTimage
```

グレースケールまたはバイナリ画像Iを開きます。

形態学的開口操作は、同じ構造要素を使用して、侵食の後に膨張を行うものです。開口は、幅`hsize`および高さ`vsize`の0と1の行列、または可能であれば構造要素`sel`を使用して実行されます。後者のケースは高速ですが、バイナリ画像のみに利用可能であり、ここでの*バイナリ*画像とは、ブール画像またはUInt8型の0と1のみを含む画像を指します。

### 引数

  * `I::Union{GMTimage{<:UInt8, 2}, GMTimage{<:Bool, 2}}`: 入力画像。

### キーワード引数

  * `hsize::Int=3`: 'ボックス'構造要素の水平サイズ。
  * `vsize::Int=3`: 'ボックス'構造要素の垂直サイズ。
  * `sel=nothing`: 構造要素（$strel$関数を参照）。`hsize`および`vsize`オプションの代替。$nothing$と等しい場合、サイズ`hsize` x `vsize`の構造ボックスが使用されます。

### 戻り値

開口が適用された、`I`と同じ型の新しい`GMTimage`。

### 例

幅20の構造ボックスを使用した開口の図示

```julia
I = gmtread(TESTSDIR * "assets/packman.png");
J = imopen(I, sel=strel("box", 20));
grdimage(I, figsize=7)
grdimage!(J, figsize=7, xshift=7.1, show=true)
```
