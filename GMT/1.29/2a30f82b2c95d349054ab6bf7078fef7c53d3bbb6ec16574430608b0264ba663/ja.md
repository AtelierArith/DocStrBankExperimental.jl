```
J = imtophat(I::Union{GMTimage{<:UInt8, 2}, GMTimage{<:Bool, 2}}; hsize=3, vsize=3)::GMTimage
```

グレースケールまたはバイナリ画像に対して形態学的トップハット操作を行います。

トップハットは画像の形態学的開口を計算し、次のようにします: `orig_image - opening`

この変換は、非均一な照明のあるグレースケール画像のコントラストを強化するために使用できます。また、画像内の小さな明るいオブジェクトを孤立させることもできます。

### 引数

  * `I::Union{GMTimage{<:UInt8, 2}, GMTimage{<:Bool, 2}}`: 入力画像。

### キーワード引数

  * `hsize::Int=3`: 'ボックス' 構造要素の水平サイズ。
  * `vsize::Int=3`: 'ボックス' 構造要素の垂直サイズ。

### 戻り値

トップハットが適用された `I` と同じタイプの新しい `GMTimage`。

### 例

トップハットフィルタリングを実行し、画像を表示します。

```julia
I = gmtread(TESTSDIR * "assets/rice.png");
J = imtophat(I, hsize=11, vsize=11);
grdimage(I, figsize=6)
grdimage!(J, figsize=6, xshift=6, show=true)
```
