```
J = imbothat(I::Union{GMTimage{<:UInt8, 2}, GMTimage{<:Bool, 2}}; hsize=3, vsize=3)::GMTimage
```

グレースケールまたはバイナリ画像に対して形態学的ボトムハット操作を行います。

ボトムハットは画像の形態学的閉じを計算し、次のようにします: `closing - orig_image` この変換は、近隣の他のピクセルよりも暗いピクセルを孤立させます。

### 引数

  * `I::Union{GMTimage{<:UInt8, 2}, GMTimage{<:Bool, 2}}`: 入力画像。

### キーワード引数

  * `hsize::Int=3`: 'ボックス' 構造要素の水平サイズ。
  * `vsize::Int=3`: 'ボックス' 構造要素の垂直サイズ。

### 戻り値

ボトムハットが適用された `I` と同じタイプの新しい `GMTimage`。
