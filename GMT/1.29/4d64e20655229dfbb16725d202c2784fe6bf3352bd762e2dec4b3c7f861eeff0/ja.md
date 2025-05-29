```
I = imreconstruct(marker::Union{Matrix{Bool}, Matrix{UInt8}}, Imask::GMTimage{<:UInt8, 2}; conn=4, insitu=true)
```

画像 `marker` を画像 `mask` の下で形態学的再構成を行います。

`marker` の要素は、対応する `mask` の要素以下でなければなりません。`marker` の値が `mask` の対応する要素より大きい場合、$imreconstruct$ は手続きを開始する前に値をマスクレベルにクリップします。形態学的処理は、Leptonica 関数 $pixSeedfillGray$ によって行われます。

### 引数

  * `marker`: 再構成される画像（再構成された画像を保持します）。これは、Boolean または UInt8 タイプの行列または $GMTimage$ であることができます。
  * `mask`: マスク画像。タイプ（$GMTimage$ または行列）は Boolean または UInt8 です。

### キーワード引数

  * `conn::Int`: 画像再構成の接続性（4 または 8）。デフォルトは 4 です。
  * `insitu::Bool`: true の場合、入力画像はインシチュとして扱われます。デフォルトは true です。

### 戻り値

  * 新しい $GMTimage$（または行列）。

### 例

再構成を使用して画像をセグメント化します。

```julia
text(["Hello World"], region=(1.92,2.08,1.97,2.02), x=2.0, y=2.0, font=(30, "Helvetica-Bold", :white),
     frame=(axes=:none, bg=:black), figsize=(6,0), name="tmp.png")
I = gmtread("tmp.png", band=1);
marker = fill(UInt8(0),(size(I)));
marker[390,130] = UInt8(255);
im = imreconstruct(Im, I)
```
