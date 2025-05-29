```
img = rgb2lab(I::GMTimage{UInt8, 3})
```

または

```
L, a, b = rgb2lab(I::GMTimage{UInt8, 3}, L=false, a=false, b=false)
```

RGBをCIE 1976 L*a*b*に変換します。

オプションとして、L、a*、b*のいずれか1つから3つのコンポーネントを別々の画像として返します。そのためには、`keywords`を使用します：`L`、`a`、または`b`。各$true$の出現はそのコンポーネントを返すことを意味し、そうでない場合は空の画像を返します。

### 引数

  * `I::GMTimage{UInt8, 3}`: 入力RGB画像。

### キーワード引数

  * `L`: `true`の場合、`L`コンポーネントを返します。
  * `a`: `true`の場合、`a`コンポーネントを返します。
  * `b`: `true`の場合、`b`コンポーネントを返します。

### 返り値

RGB $GMTimage$または最大3つの$GMTimages$グレースケール画像（L、a*、b*コンポーネントを含む）。

### 例

```julia
# RGB画像を読み込み、Lab変換を計算します。
I = gmtread(GMT.TESTSDIR * "assets/seis_section_rgb.jpg");
Ilab = rgb2lab(I);

# L、a*、b*コンポーネント
L,a,b = rgb2lab(I, L=true, a=true, b=true);

# 5つを表示します。
grdimage(I, figsize=8)
grdimage!(Ilab, figsize=8, yshift=-3.8)
grdimage!(L, figsize=8, yshift=-3.8)
grdimage!(a, figsize=8, yshift=-3.8)
grdimage!(b, figsize=8, yshift=-3.8, show=true)
```
