```
J = imdilate(I::Union{GMTimage{<:UInt8, 2}, GMTimage{<:Bool, 2}}; hsize=3, vsize=3, sel=nothing)::GMTimage
```

グレースケールまたはバイナリ画像Iを膨張させます。

膨張は、幅`hsize`および高さ`vsize`の0と1の行列、または可能であれば構造要素`sel`を使用して行われます。後者のケースは高速ですが、バイナリ画像のみに利用可能であり、ここでの*バイナリ*画像とは、Boolean画像またはUInt8型の0と1のみを含む画像を指します。

### 引数

  * `I::Union{GMTimage{<:UInt8, 2}, GMTimage{<:Bool, 2}}`: 入力画像。

### キーワード引数

  * `hsize::Int=3`: 'ボックス'構造要素の横サイズ。
  * `vsize::Int=3`: 'ボックス'構造要素の縦サイズ。
  * `sel=nothing`: 構造要素（$strel$関数を参照）。`hsize`および`vsize`オプションの代替。$nothing$に等しい場合、サイズ`hsize` x `vsize`の構造ボックスが使用されます。

### 戻り値

膨張が適用された、`I`と同じ型の新しい`GMTimage`。

### 例

幅3の正方形による膨張（`sel`、`hsize`、`vsize`のいずれも指定されていない場合のデフォルト）

```julia
I = gmtread(TESTSDIR * "assets/fig_text_bw.png");
J = imdilate(I);
grdimage(I, figsize=7)
grdimage!(J, figsize=7, xshift=7.1, show=true)
```
