```
J = imcomplement(I::GMTimage) -> GMTimage
```

画像 `I` の補完を計算し、結果を `J` に返します。

`I` はバイナリ、強度、または真の色の画像である可能性があります。`J` は `I` と同じタイプとサイズです。`I` は単なる行列でもかまいません。すべての数値型（ただし複素数は除く）が許可されています。

バイナリ画像の補完では、黒は白になり、白は黒になります。グレースケールまたは真の色の画像の場合、暗い領域は明るくなり、明るい領域は暗くなります。

$$
imcomplement!
$$

関数はインプレースで動作し、修正された $I$ を返します。

### 返り値

修正された $I$ 画像。

### 例

```jldoctest
text(["Hello World"], region=(1.92,2.08,1.97,2.02), x=2.0, y=2.0,
     font=(30, "Helvetica-Bold", :white),
     frame=(axes=:none, bg=:black), figsize=(6,0), name="tmp.png")

# 1つのバンドのみを読み込む（グレースケールであっても、"tmp.png" は実際にはRGB）
I = gmtread("tmp.png", band=1);
Ic = imcomplement(I);

# 2つを表示
grdimage(I, figsize=8)
grdimage!(Ic, figsize=8, yshift=-2.57, show=true)
```
