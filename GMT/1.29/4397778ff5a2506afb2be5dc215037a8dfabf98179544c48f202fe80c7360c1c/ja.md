```
YCbCr = rgb2YCbCr(I::GMTimage{UInt8, 3}; Y=false, Cb=false, Cr=false, BT709=false)
```

または

```
Y,Cb,Cr = rgb2YCbCr(I::GMTimage{UInt8, 3}; Y=false, Cb=false, Cr=false, BT709=false)
```

RGBカラー値をYCbCr画像の輝度（Y）およびクロミナンス（CbおよびCr）値に変換します。

オプションとして、Y、Cb、Crのいずれか1つから3つを別々の画像で返すことができます。そのためには、`keywords`を使用します：`Y`、`Cb`、または`Cr`。各$true$の出現はその成分を返すようにし、それ以外は空の画像を返します。代替の$rgb2ycbcr$エイリアス（すべて小文字）も受け付けられます。

### 引数

  * `I::GMTimage{UInt8, 3}`: 入力RGB画像。

### キーワード引数

  * `Y`: `true`の場合、輝度（Y）成分を返します。
  * `Cb`: `true`の場合、Cb成分を返します。
  * `Cr`: `true`の場合、Cr成分を返します。
  * `BT709`: `true`の場合、デフォルトの$ITU-R BT.601$の代わりに$ITU-R BT.709$変換を使用します。詳細は https://en.wikipedia.org/wiki/YCbCr を参照してください。

### 返り値

輝度（Y）、CbおよびCr成分を持つRGB $GMTimage$または最大3つの$GMTimages$グレースケール画像。

### 例

```julia

# RGB画像を読み込む
I = gmtread(GMT.TESTSDIR * "assets/seis_section_rgb.jpg");
Iycbcr = rgb2YCbCr(I);

# CbおよびCr成分
_,Cb,Cr = rgb2YCbCr(I, Cb=true, Cr=true);

# 4つを表示する。
grdimage(I, figsize=6)
grdimage!(Iycbcr, figsize=6, yshift=-2.84)
grdimage!(Cb, figsize=6, yshift=-2.84)
grdimage!(Cr, figsize=6, yshift=-2.84, show=true)
```
