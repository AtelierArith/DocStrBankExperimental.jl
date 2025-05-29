```
S = streamlines(U::GMTgrid, V::GMTgrid, startX, startY; step=0.1, max_vert::Int=10000)
```

2次元のストリームラインをベクトルフィールドの2次元行列（実際にはGMTdataset）として計算します。入力の`U`と`V`は、`x`および`y`の速度成分を持つGMTgridであり、`startX`と`startY`はストリームラインの開始位置です。`step`はベクトルデータを補間するためのデータ単位でのステップサイズで、`max_vert`はストリームライン内の最大頂点数です。`startX`と`startY`はスカラー、ベクトル、または一方がスカラーで他方がベクトルであることができます。ストリームラインを持つVector{GMTdataset}を返します。

```
S = streamlines(U::GMTgrid, V::GMTgrid, D::GMTdataset; step=0.1, max_vert::Int=10000)
```

このメソッドでは、ストリームラインの開始位置が`D`引数の2列から取得されます。ストリームラインを持つVector{GMTdataset}を返します。

```
S, A = streamlines(U::GMTgrid, V::GMTgrid; step=0.1, max_vert::Int=10000)
```

2DグリッドUとVから自動的に間隔を空けたストリームラインを計算するメソッドです。ストリームラインは`S` Vector{GMTdataset}に格納され、`A`は必要に応じて矢印の頭をプロットするためのストリームラインに沿った位置を保持します。

```
S = streamlines(U::GMTgrid, V::GMTgrid; side::Union{String, Symbol}="left", step=0.1, max_vert::Int=10000)
```

ここでは、グリッドの4つの側面のうちの1つに沿った開始位置を自動生成します。`side`キーワードで希望する側を選択します。ストリームラインを持つVector{GMTdataset}を返します。

```
S = streamlines(x, y, U::Matrix, V::Matrix, sx, sy; step=0.1, max_vert::Int=10000)
```

この最後の2Dメソッドでは、ユーザーが`x`および`y`のベクトルデータ座標を渡すことができ、UとVは速度データを持つ行列であり、残りの引数は他のメソッドと同じ意味を持ちます。ストリームラインを持つVector{GMTdataset}を返します。

```
S = streamlines(x::Matrix, y::Matrix, U::Matrix, V::Matrix; step=0.1, max_vert::Int=10000)
```

`x`と`y`は、*x*および*y*の開始座標を持つメッシュグリッドであると仮定されます。

```
S = streamlines(U::GMTgrid, V::GMTgrid, W::GMTgrid, startX, startY, startZ; step=0.1, max_vert::Int=10000)
```

ストリームラインを持つ3Dベクトルフィールドのボリュームを計算します。ここで`U`、`V`、および`W`は、`x`、`y`、`z`の速度成分を持つ3Dキューブです。`startX`、`startY`、および`startZ`はスカラーまたはベクトル座標配列であることができます。ストリームラインを持つVector{GMTdataset}を返します。

### 例

```
x,y = GMT.meshgrid(-10:10);
u = 2 .* x .* y;
v = y .^2 - x .^ 2;
U = mat2grid(u, x[1,:], y[:,1]);
V = mat2grid(v, x[1,:], y[:,1]);
r,a = streamlines(U, V);
plot(r, decorated=(locations=a, symbol=(custom="arrow", size=0.3), fill=:black, dec2=true), show=1)
```
