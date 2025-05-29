```
findpeaks(y, x=1:length(y); min_height=minimum(y), min_prom=minimum(y), min_dist=0, threshold=0; xsorted::Bool=false)
findpeaks(D::GMTdataset; min_height=minimum(y), min_prom=minimum(y), min_dist=0, threshold=0; xsorted::Bool=false)
```

1Dの実数配列における局所的な最大値のインデックスを返します。MATLABのfindpeaks()に似ています。

局所的なピークは、隣接する2つのサンプルよりも大きいか、Infと等しいデータサンプルです。ピークは出現順に出力されます。この関数は$Findpeaks.jl$ (https://github.com/tungli/Findpeaks.jl)パッケージからのものです。

### 引数

  * `y`: ベクトルとして指定された入力データ。`y`は実数であり、少なくとも3つの要素を持つ必要があります。
  * `x`: ベクトルまたは日時配列として指定された位置。`x`は単調増加し、`y`と同じ長さである必要があります。`x`が省略された場合、`y`のインデックスが位置として使用されます。
  * `D`: `y`と`x`の代わりに、2つの列（`x,y`またはそれ以上）を持つ`GMTdataset`を提供できます。

### キーワード引数

  * `min_height`: 最小ピーク高さ、実数スカラーとして指定されます。この引数を使用して、$findpeaks$が`min_height`より高いピークのみを返すようにします。
  * `min_prom`: 最小ピークの重要度、非負の実数スカラーとして指定されます。この引数を使用して、$findpeaks$が相対的重要度が少なくとも`min_prom`であるピークのみを返すようにします（https://www.mathworks.com/help/signal/ref/findpeaks.html#buff2uuを参照）。
  * `min_dist`: 最小ピーク間隔（最高のピークを保持）。このオプションに値を指定すると、アルゴリズムは最も高いピークを選択し、そのピークから`min_dist`以内のすべてのピークを無視します。
  * `threshold`: ピークと隣接点の間の最小差（絶対値）。この引数を使用して、$findpeaks$が隣接する値を少なくとも`threshold`の値だけ超えるピークのみを返すようにします。
  * `xsorted`: trueの場合、局所的な最大値のインデックスは`x`の昇順にソートされます。デフォルトは振幅でソートします。

### 戻り値

  * `peaks`: 局所的な最大値のインデックス（`xsorted=false`の場合は最高のピークから最低のピークにソートされています）。

### 例

```julia
D = gmtread(TESTSDIR * "assets/example_spectrum.txt");
peaks = findpeaks(D, min_prom=1000.);
plot(D, title="顕著なピーク")
scatter!(D[peaks,:], mc=:red, show=true)
```
