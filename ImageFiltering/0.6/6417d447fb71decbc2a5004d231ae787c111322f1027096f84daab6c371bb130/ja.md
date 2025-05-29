```julia
    imgradients(img, kernelfun=KernelFactors.ando3, border="replicate") -> gimg1, gimg2, ...
```

画像のすべての点で、`kernelfun`で指定されたカーネルを使用して、`img`の1次元目と2次元目の方向の勾配を推定します。

# 出力

勾配は、入力の各次元に対して1つの配列からなるタプルとして返されます。`gimg1`は1次元目に関する導関数に対応し、`gimg2`は2次元目に対応し、以下同様です。

# 詳細

さまざまな勾配推定方法の違いを理解するためには、次の2つを区別することが役立ちます：(1) 連続スカラー値の*アナログ*画像 $f_\textrm{A}(x_1,x_2)$、ここで $x_1,x_2 \in \mathbb{R}$、および (2) その離散*デジタル*実現 $f_\textrm{D}(x_1',x_2')$、ここで $x_1',x_2' \in \mathbb{N}$、$1 \le x_1' \le M$ および $1 \le x_2' \le N$。

## アナログ画像

位置 $(x_1,x_2)$ における連続アナログ画像 $f_{\textrm{A}}(x_1,x_2)$ の勾配は、次のベクトルとして定義されます。

$$
\nabla \mathbf{f}_{\textrm{A}}(x_1,x_2) = \frac{\partial
f_{\textrm{A}}(x_1,x_2)}{\partial x_1} \mathbf{e}_{1} +
\frac{\partial f_{\textrm{A}}(x_1,x_2)}{\partial x_2} \mathbf{e}_{2},
$$

ここで $\mathbf{e}_{d}$ $(d = 1,2)$ は $x_d$方向の単位ベクトルです。勾配は、座標 $(x_1,x_2)$ における $f_{\textrm{A}}$ の最大変化率の方向を指します。勾配は、任意の方向における関数の導関数を計算するために使用できます。特に、単位ベクトル $\mathbf{u}$ の方向における $f_{\textrm{A}}$ の導関数は、$\nabla_{\mathbf{u}}f_\textrm{A}(x_1,x_2) = \nabla \mathbf{f}_{\textrm{A}}(x_1,x_2) \cdot \mathbf{u}$ で与えられ、ここで $\cdot$ は内積を示します。

## デジタル画像

実際には、光の強度が離散的な位置のセットでのみ知られているデジタル画像 $f_\textrm{D}(x_1',x_2')$ を取得します。これは、必要な偏微分が未定義であり、離散差分公式を使用して近似する必要があることを意味します [1]。

偏微分を近似する簡単な方法は、中心差分公式を使用することです。

$$
 \frac{\partial f_{\textrm{D}}(x_1',x_2')}{\partial x_1'}  \approx
        \frac{f_{\textrm{D}}(x_1'+1,x_2') - f_{\textrm{D}}(x_1'-1,x_2') }{2}
$$

および

$$
 \frac{\partial f_{\textrm{D}}(x_1',x_2')}{\partial x_2'}   \approx
         \frac{f_{\textrm{D}}(x_1',x_2'+1) - f_{\textrm{D}}(x_1',x_2'-1)}{2}.
$$

ただし、中心差分公式はノイズに非常に敏感です。ノイズの多い画像データを扱う場合、隣接する画像強度の適切な重み付き組み合わせを使用することで、偏微分のより良い近似を得ることができます。重み付き組み合わせは、画像と必要な重みを特徴付ける*カーネル*との間の*離散畳み込み*操作として表現できます。特に、$h_{x_d}$ ($d = 1,2)$ が $2r+1 \times 2r+1$ カーネルを表す場合、次のようになります。

$$
 \frac{\partial f_{\textrm{D}}(x_1',x_2')}{\partial x_d'}  \approx
\sum_{i = -r}^r \sum_{j = -r}^r
f_\textrm{D}(x_1'-i,x_2'-j)
  h_{x_d}(i,j).
$$

カーネルは、しばしば*マスク*または*畳み込み行列*とも呼ばれます。

### 重み付けスキームと近似誤差

重みの選択は、近似誤差の大きさと有限差分スキームが*等方的*であるかどうかを決定します。有限差分スキームが等方的であるとは、近似誤差が座標系の向きに依存しない場合を指し、*異方的*であるとは、近似誤差に方向的バイアスがある場合を指します [2]。連続アナログ画像では、勾配の大きさは座標系の回転に対して不変ですが、実際には有限の離散点のセットで完全な等方性を得ることはできません。したがって、有限差分スキームは、近似における主な誤差項が好ましい方向を持たない場合、通常は等方的と見なされます。

画像処理で使用されるほとんどの有限差分スキームは $3 \times 3$ カーネルに基づいており、[7] によると、多くは次のように単一のパラメータ $\alpha$ でパラメータ化することもできます。

$$
\mathbf{H}_{x_{1}} =
\frac{1}{4 + 2\alpha}
\begin{bmatrix}
-1 & -\alpha & -1 \\
0 & 0 & 0 \\
 1 & \alpha & 1
\end{bmatrix}
\quad
\text{および}
\quad
\mathbf{H}_{x_{2}} =
\frac{1}{2 + 4\alpha}
\begin{bmatrix}
-1 & 0 & 1 \\
-\alpha & 0 & \alpha \\
 -1 & 0 & 1
\end{bmatrix},
$$

ここで

$$
\alpha =
\begin{cases}
0,  & \text{単純有限差分}; \\
1, &  \text{プレウィット}; \\
2, &  \text{ソーベル}; \\
2.4351, &  \text{安藤}; \\
\frac{10}{3}, &  \text{シャール}; \\
4, &  \text{ビックリー}.
\end{cases}
$$

## 可分カーネル

カーネルは、2つの1次元フィルタの畳み込みとして表現できる場合に*可分*と呼ばれます。カーネルの行列表現では、可分性はカーネル行列が2つのベクトルの外積として書かれることを意味します。可分カーネルは計算上の利点を提供します。なぜなら、2次元の畳み込みを行う代わりに、1次元の畳み込みのシーケンスを実行できるからです。

# オプション

`kernelfun` パラメータを介して有限差分スキームの選択を指定できます。また、`border` パラメータを使用して画像の境界上のピクセルをどのように処理するかを示すこともできます。

## `kernelfun` の選択肢

一般に、`kernelfun` は次のインターフェースを満たす任意の関数であることができます。

```julia
    kernelfun(extended::NTuple{N,Bool}, d) -> kern_d,
```

ここで `kern_d` は、$N$次元配列の$d$次元に関する導関数を生成するためのカーネルです。パラメータ `extended[i]` は、次元 $i$ に沿った画像のサイズが > 1 の場合に真です。パラメータ `kern_d` は、密なカーネルまたは因子化されたカーネルとして提供される場合があり、カーネルが可分である場合は因子化された表現が推奨されます。

以下に、いくつかの有効な `kernelfun` オプションを示します。

### `KernelFactors.prewitt`

*プレウィット*オプション [3] では、勾配の計算は次のカーネルに基づいています。

$$
\begin{aligned}
\mathbf{H}_{x_1} & = \frac{1}{6}
    \begin{bmatrix}
    -1 & -1 & -1 \\
    0 & 0 & 0 \\
    1 & 1 & 1
    \end{bmatrix}
&
\mathbf{H}_{x_2} & =  \frac{1}{6}
    \begin{bmatrix}
    -1 & 0 & 1 \\
    -1 & 0 & 1 \\
    -1 & 0 & 1
    \end{bmatrix} \\
& = \frac{1}{6}
    \begin{bmatrix}
    1 \\
    1  \\
    1
    \end{bmatrix}
    \begin{bmatrix}
    -1 & 0 & 1
    \end{bmatrix}
&
& = \frac{1}{6}
    \begin{bmatrix}
    -1 \\
    0  \\
    1
    \end{bmatrix}
    \begin{bmatrix}
    1 & 1 & 1
    \end{bmatrix}.
\end{aligned}
$$

参照: [`KernelFactors.prewitt`](@ref) および [`Kernel.prewitt`](@ref)

### `KernelFactors.sobel`

*ソーベル*オプション [4] は、次のカーネルを指定します。

$$
\begin{aligned}
\mathbf{H}_{x_1} & = \frac{1}{8}
    \begin{bmatrix}
    -1 & -2 & -1 \\
     0 & 0 & 0 \\
     1 & 2 & 1
    \end{bmatrix}
&
\mathbf{H}_{x_2} & = \frac{1}{8}
    \begin{bmatrix}
    -1 & 0 & 1 \\
    -2 & 0 & 2 \\
    -1 & 0 & 1
    \end{bmatrix} \\
& = \frac{1}{8}
    \begin{bmatrix}
    -1 \\
    0  \\
    1
    \end{bmatrix}
    \begin{bmatrix}
    1 & 2 & 1
    \end{bmatrix}
&
& = \frac{1}{8}
    \begin{bmatrix}
    1 \\
    2  \\
    1
    \end{bmatrix}
    \begin{bmatrix}
    -1 & 0 & 1
    \end{bmatrix}.
\end{aligned}
$$

参照:  [`KernelFactors.sobel`](@ref) および [`Kernel.sobel`](@ref)

### `KernelFactors.ando3`

*安藤3*オプション [5] は、次のカーネルを指定します。

$$
\begin{aligned}
\mathbf{H}_{x_1} &  =
    \begin{bmatrix}
    -0.112737 & -0.274526 & -0.112737 \\
     0 & 0 & 0 \\
     0.112737 & 0.274526 & 0.112737
    \end{bmatrix}
&
\mathbf{H}_{x_2}  & =
    \begin{bmatrix}
    -0.112737 & 0 & 0.112737 \\
    -0.274526 & 0 & 0.274526 \\
    -0.112737 & 0 & 0.112737
    \end{bmatrix} \\
&  = \begin{bmatrix}
    -1 \\
    0  \\
    1
    \end{bmatrix}
    \begin{bmatrix}
    0.112737 & 0.274526 & 0.112737
    \end{bmatrix}
&
&  = \begin{bmatrix}
    0.112737 \\
    0.274526  \\
    0.112737
    \end{bmatrix}
    \begin{bmatrix}
    -1 & 0 & 1
    \end{bmatrix}.
\end{aligned}
$$

参照:  [`KernelFactors.ando3`](@ref)、および [`Kernel.ando3`](@ref);  [`KernelFactors.ando4`](@ref)、および [`Kernel.ando4`](@ref); [`KernelFactors.ando5`](@ref)、および [`Kernel.ando5`](@ref)

### `KernelFactors.scharr`

*シャール*オプション [6] は、次のカーネルを指定します。

$$
\begin{aligned}
\mathbf{H}_{x_{1}} & =
\frac{1}{32}
\begin{bmatrix}
-3 & -10 & -3 \\
0 & 0 & 0 \\
 3 & 10 & 3
\end{bmatrix}
&
\mathbf{H}_{x_{2}} & =
\frac{1}{32}
\begin{bmatrix}
-3 & 0 & 3 \\
-10 & 0 & 10\\
-3 & 0 & 3
\end{bmatrix} \\
& = \frac{1}{32}
\begin{bmatrix}
    -1 \\
    0  \\
    1
\end{bmatrix}
\begin{bmatrix}
    3 & 10 & 3
\end{bmatrix}
&
& = \frac{1}{32}
\begin{bmatrix}
    3 \\
    10  \\
    3
\end{bmatrix}
\begin{bmatrix}
    -1 & 0 & 1
\end{bmatrix}.
\end{aligned}
$$

参照:  [`KernelFactors.scharr`](@ref) および [`Kernel.scharr`](@ref)

### `KernelFactors.bickley`

*ビックリー*オプション [7,8] は、次のカーネルを指定します。

$$
\begin{aligned}
\mathbf{H}_{x_1} & = \frac{1}{12}
    \begin{bmatrix}
        -1 & -4 & -1 \\
         0 & 0 & 0 \\
         1 & 4 & 1
    \end{bmatrix}
&
\mathbf{H}_{x_2} & = \frac{1}{12}
    \begin{bmatrix}
        -1 & 0 & 1 \\
        -4 & 0 & 4 \\
        -1 & 0 & 1
    \end{bmatrix} \\
& = \frac{1}{12}
    \begin{bmatrix}
        -1 \\
        0  \\
        1
    \end{bmatrix}
    \begin{bmatrix}
        1 & 4 & 1
    \end{bmatrix}
&
&  = \frac{1}{12}
   \begin{bmatrix}
        1 \\
        4  \\
        1
   \end{bmatrix}
   \begin{bmatrix}
        -1 & 0 & 1
   \end{bmatrix}.
\end{aligned}
$$

参照:  [`KernelFactors.bickley`](@ref) および [`Kernel.bickley`](@ref)

## `border` の選択肢

画像の端では、`border` を使用して、元の境界を超えて画像を外挿するために使用されるパディングを指定します。各オプションの指標例として、アルファベット順に指定された6つのピクセルの行からなる画像のパディングの結果を示します: $\boxed{a \, b \, c \, d \, e \, f}$. 左右の境界に対するパディングの影響のみを示しますが、上下の境界にも同様の結果が適用されます。

### `"replicate"`

境界ピクセルは画像の境界を超えて拡張されます。

$$
\boxed{
\begin{array}{l|c|r}
  a\, a\, a\, a  &  a \, b \, c \, d \, e \, f & f \, f \, f \, f
\end{array}
}
$$

参照: [`Pad`](@ref)、[`padarray`](@ref)、[`Inner`](@ref) および [`NoPad`](@ref)

### `"circular"`

境界ピクセルはラップします。たとえば、左の境界を超えてインデックスを付けると、右の境界から始まる値が返されます。

$$
\boxed{
\begin{array}{l|c|r}
  c\, d\, e\, f  &  a \, b \, c \, d \, e \, f & a \, b \, c \, d
\end{array}
}
$$

参照: [`Pad`](@ref)、[`padarray`](@ref)、[`Inner`](@ref) および [`NoPad`](@ref)

### `"symmetric"`

境界ピクセルはピクセル間の位置に対して反射します。つまり、ミラーリング時に境界ピクセルは省略されます。

$$
\boxed{
\begin{array}{l|c|r}
  e\, d\, c\, b  &  a \, b \, c \, d \, e \, f & e \, d \, c \, b
\end{array}
}
$$

参照: [`Pad`](@ref)、[`padarray`](@ref)、[`Inner`](@ref) および [`NoPad`](@ref)

### `"reflect"`

境界ピクセルはエッジ自体に対して反射します。

$$
\boxed{
\begin{array}{l|c|r}
  d\, c\, b\, a  &  a \, b \, c \, d \, e \, f & f \, e \, d \, c
\end{array}
}
$$

参照: [`Pad`](@ref)、[`padarray`](@ref)、[`Inner`](@ref) および [`NoPad`](@ref)

# 例

この例では、勾配の方向がどれだけ正確に推定されるかという観点から、勾配推定方法の品質を比較します。

```julia
using Images

values = LinRange(-1,1,128);
w = 1.6*pi;

# 関数 f(x,y) = sin( (w*x)^2 + (w*y)^2 ) の定義とその正確な偏微分。
I = [sin( (w*x)^2 + (w*y)^2 ) for y in values, x in values];
Ix = [2*w*x*cos( (w*x)^2 + (w*y)^2 ) for y in values, x in values];
Iy = [2*w*y*cos( (w*x)^2 + (w*y)^2 ) for y in values, x in values];

# 勾配の正確な方向を決定します。
direction_true = atan.(Iy./Ix);

for kernelfunc in (KernelFactors.prewitt, KernelFactors.sobel,
                   KernelFactors.ando3, KernelFactors.scharr,
                   KernelFactors.bickley)

    # 勾配とその方向を推定します。
    Gy, Gx = imgradients(I,kernelfunc, "replicate");
    direction_estimated = atan.(Gy./Gx);

    # 推定された方向と真の方向の間の平均絶対偏差を決定します。
    # 境界の値は誤っていると予想されるため、無視します。
    error = mean(abs.(direction_true[2:end-1,2:end-1] -
                     direction_estimated[2:end-1,2:end-1]));

    error = round(error, digits=5);
    println("Using $kernelfunc results in a mean absolute deviation of $error")
end

# 出力

Using ImageFiltering.KernelFactors.prewitt results in a mean absolute deviation of 0.01069
Using ImageFiltering.KernelFactors.sobel results in a mean absolute deviation of 0.00522
Using ImageFiltering.KernelFactors.ando3 results in a mean absolute deviation of 0.00365
Using ImageFiltering.KernelFactors.scharr results in a mean absolute deviation of 0.00126
Using ImageFiltering.KernelFactors.bickley results in a mean absolute deviation of 0.00038
```

# 参考文献

1. B. Jahne, *Digital Image Processing* (5th ed.). Springer Publishing Company, Incorporated, 2005. [10.1007/3-540-27563-0](https://doi.org/10.1007/3-540-27563-0)
2. M. Patra  and  M. Karttunen, "Stencils with isotropic discretization error for differential operators," *Numer. Methods Partial Differential Eq.*, vol. 22, pp. 936–953, 2006. [doi:10.1002/num.20129](https://doi.org/doi:10.1002/num.20129)
3. J. M. Prewitt, "Object enhancement and extraction," *Picture processing and Psychopictorics*, vol. 10, no. 1, pp. 15–19, 1970.
4. P.-E. Danielsson and O. Seger, "Generalized and separable sobel operators," in  *Machine Vision for Three-Dimensional Scenes*,  H. Freeman, Ed.  Academic Press, 1990,  pp. 347–379. [doi:10.1016/b978-0-12-266722-0.50016-6](https://doi.org/doi:10.1016/b978-0-12-266722-0.50016-6)
5. S. Ando, "Consistent gradient operators," *IEEE Transactions on Pattern Analysis and Machine Intelligence*, vol. 22, no.3, pp. 252–265, 2000. [doi:10.1109/34.841757](https://doi.org/doi:10.1109/34.841757)
6. H. Scharr and  J. Weickert, "An anisotropic diffusion algorithm with optimized rotation invariance," *Mustererkennung 2000*, pp. 460–467, 2000. [doi:10.1007/978-3-642-59802-9_58](https://doi.org/doi:10.1007/978-3-642-59802-9_58)
7. A. Belyaev, "Implicit image differentiation and filtering with applications to image sharpening," *SIAM Journal on Imaging Sciences*, vol. 6, no. 1, pp. 660–679, 2013. [doi:10.1137/12087092x](https://doi.org/doi:10.1137/12087092x)
8. W. G. Bickley, "Finite difference formulae for the square lattice," *The Quarterly Journal of Mechanics and Applied Mathematics*, vol. 1, no. 1, pp. 35–42, 1948.  [doi:10.1093/qjmam/1.1.35](https://doi.org/doi:10.1093/qjmam/1.1.35)

---
