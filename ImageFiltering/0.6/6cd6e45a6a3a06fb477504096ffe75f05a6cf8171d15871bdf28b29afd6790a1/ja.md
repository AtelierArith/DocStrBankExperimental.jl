```
imfilter([T], img, kernel, [border="replicate"], [alg]) --> imgfilt
imfilter([r], img, kernel, [border="replicate"], [alg]) --> imgfilt
imfilter(r, T, img, kernel, [border="replicate"], [alg]) --> imgfilt
```

1次元、2次元または多次元配列 `img` を `kernel` でフィルタリングし、相関を計算します。

# 詳細

*フィルタリング* という用語は、画像のフーリエ変換の文脈で現れ、画像をその標準的な空間領域から対応する周波数領域にマッピングします。周波数領域で画像を操作することは、特定の周波数成分を保持または破棄することに相当します。このプロセスは、ふるい分けやフィルタリングに類似しています[1]。フーリエ変換は、画像の空間表現と周波数表現の間にリンクを確立するため、空間領域でのさまざまな画像操作を特定の周波数を受け入れたり拒否したりするフィルタリング操作として解釈できます。

*空間フィルタリング* というフレーズは、操作が少なくとも概念的に画像の空間領域の文脈で考案されていることを強調するために使用されます。線形空間フィルタリングと非線形空間フィルタリングの区別もあります。ピクセルに対して行われる操作が線形であればフィルタは線形と呼ばれ、そうでなければ非線形とラベル付けされます。

画像フィルタは次の関数で表現できます。

$$
 w: \{s\in \mathbb{Z} \mid -k_1 \le s \le k_1  \} \times  \{t \in \mathbb{Z} \mid -k_2 \le t \le k_2  \}   \rightarrow \mathbb{R},
$$

ここで $k_i  \in \mathbb{N}$ (i = 1,2) です。一般的に $k_1 = 2a+1$ および $k_2 = 2b + 1$ と定義され、ここで $a$ と $b$ は整数であり、フィルタの次元が奇数サイズであることを保証します。通常、$k_1$ は $k_2$ と等しく、下付き文字を省略して $k \times k$ フィルタと呼ばれます。フィルタのドメインは空間座標のグリッドを表すため、フィルタはしばしばマスクと呼ばれ、グリッドとして視覚化されます。たとえば、$3 \times 3$ マスクは次のように描写できます。

$$
\scriptsize
\begin{matrix}
\boxed{
\begin{matrix}
\phantom{w(-9,-9)} \\
w(-1,-1) \\
\phantom{w(-9,-9)} \\
\end{matrix}
}

&

\boxed{
\begin{matrix}
\phantom{w(-9,-9)} \\
w(-1,0) \\
\phantom{w(-9,-9)} \\
\end{matrix}
}
 &
\boxed{
\begin{matrix}
\phantom{w(-9,-9)} \\
w(-1,1) \\
\phantom{w(-9,-9)} \\
\end{matrix}
}
\\
\\
\boxed{
\begin{matrix}
\phantom{w(-9,-9)} \\
w(0,-1) \\
\phantom{w(-9,-9)} \\
\end{matrix}
}

&

\boxed{
\begin{matrix}
\phantom{w(-9,-9)} \\
w(0,0) \\
\phantom{w(-9,-9)} \\
\end{matrix}
}
 &
\boxed{
\begin{matrix}
\phantom{w(-9,-9)} \\
w(0,1) \\
\phantom{w(-9,-9)} \\
\end{matrix}
}
\\
\\
\boxed{
\begin{matrix}
\phantom{w(-9,-9)} \\
w(1,-1) \\
\phantom{w(-9,-9)} \\
\end{matrix}
}

&

\boxed{
\begin{matrix}
\phantom{w(-9,-9)} \\
w(1,0) \\
\phantom{w(-9,-9)} \\
\end{matrix}
}
 &
\boxed{
\begin{matrix}
\phantom{w(-9,-9)} \\
w(1,1) \\
\phantom{w(-9,-9)} \\
\end{matrix}
}
\end{matrix}.
$$

$$
w(s,t)
$$

の値は *フィルタ係数* と呼ばれます。

## 離散畳み込みと相関

画像にフィルタを適用する際に定期的に行う2つの基本的で密接に関連した操作があります。これらの操作は、離散 *相関* と *畳み込み* と呼ばれます。

相関操作は、記号 $\star$ で示され、2次元では次の式で表されます。

$$
\begin{aligned}
g(x,y) = w(x,y) \star f(x,y) = \sum_{s = -a}^{a} \sum_{t=-b}^{b} w(s,t) f(x+s, y+t),
\end{aligned}
$$

一方、対応する畳み込み操作は、記号 $\ast$ で示され、2次元では次のように表されます。

$$
\begin{aligned}
h(x,y) = w(x,y) \ast f(x,y) = \sum_{s = -a}^{a} \sum_{t=-b}^{b} w(s,t) f(x-s, y-t).
\end{aligned}
$$

デジタル画像は有限の範囲を持つため、これらの操作は画像の境界で未定義です。特に、サイズが $M \times N$ の画像に対して、関数 $f(x \pm s, y \pm t)$ は $1 \le x \pm s \le N$ および $1 \le y \pm t \le M$ の場合にのみ定義されます。実際には、この問題に対処するために、画像のドメインを人工的に拡張します。たとえば、画像をゼロでパディングすることができます。他のパディング戦略も可能であり、これらはこのドキュメントの *オプション* セクションで詳しく説明されています。

## 1次元の例

相関と畳み込みの違いは、[1] から適応した1次元の例を用いることで最もよく理解できます。フィルタ $w:\{-1,0,1\}\rightarrow \mathbb{R}$ が次の係数を持つとします。

$$
\begin{matrix}
\boxed{1} & \boxed{2} & \boxed{3}
\end{matrix}.
$$

ゼロでパディングされた離散単位インパルス関数 $f: \{x \in \mathbb{Z} \mid 1 \le x \le 7  \} \rightarrow \{0,1\}$ を考えます。この関数は画像として視覚化できます。

$$
\boxed{
\begin{matrix}
0 & \boxed{0} & \boxed{0} & \boxed{0} & \boxed{1} & \boxed{0} & \boxed{0} & \boxed{0} & 0
\end{matrix}}.
$$

相関操作は、$w$ を画像に沿ってスライドさせ、各位置での積の合計を計算することとして解釈できます。たとえば、

$$
\begin{matrix}
0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 \\
1 & 2 & 3  &  & & & & & \\
& 1 & 2 & 3  &  & & & &  \\
& & 1 & 2 & 3  &  & & &  \\
& & & 1 & 2 & 3  &  & &  \\
& & & & 1 & 2 & 3  &  &  \\
& & & & & 1 & 2 & 3  &  \\
& & & & & & 1 & 2 & 3,
\end{matrix}
$$

は出力 $g: \{x \in \mathbb{Z} \mid 1 \le x \le 7  \} \rightarrow \mathbb{R}$ を生成し、デジタル画像として視覚化すると次のようになります。

$$
\boxed{
\begin{matrix}
\boxed{0} & \boxed{0} & \boxed{3} & \boxed{2} & \boxed{1} & \boxed{0} & \boxed{0}
\end{matrix}}.
$$

畳み込み操作の解釈は相関と類似していますが、フィルタ $w$ が180度回転されています。特に、

$$
\begin{matrix}
0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 \\
3 & 2 & 1  &  & & & & & \\
& 3 & 2 & 1  &  & & & &  \\
& & 3 & 2 & 1  &  & & &  \\
& & & 3 & 2 & 1  &  & &  \\
& & & & 3 & 2 & 1  &  &  \\
& & & & & 3 & 2 & 1  &  \\
& & & & & & 3 & 2 & 1,
\end{matrix}
$$

は出力 $h: \{x \in \mathbb{Z} \mid 1 \le x \le 7  \} \rightarrow \mathbb{R}$ を生成し、次のようになります。

$$
\boxed{
\begin{matrix}
\boxed{0} & \boxed{0} & \boxed{1} & \boxed{2} & \boxed{3} & \boxed{0} & \boxed{0}
\end{matrix}}.
$$

フィルタマスクを回転させる代わりに、$f$ を回転させても同じ畳み込み結果を得ることができます。実際、畳み込みの従来の表記法は、$f$ が反転され、$w$ が反転されないことを示しています。$w$ が対称であれば、畳み込みと相関は同じ結果を与えます。

### 2次元の例

2次元の例として、フィルタ $w:\{-1, 0 ,1\} \times  \{-1,0,1\} \rightarrow \mathbb{R}$ が次の係数を持つとします。

$$
 \begin{matrix}
 \boxed{1} & \boxed{2} & \boxed{3} \\ \\
 \boxed{4} & \boxed{5} & \boxed{6} \\ \\
 \boxed{7} & \boxed{8} & \boxed{9}
 \end{matrix},
$$

そして、ゼロでパディングされた2次元離散単位インパルス関数

$$
 f:\{x \in \mathbb{Z} \mid 1 \le x \le 7  \} \times  \{y \in \mathbb{Z} \mid 1 \le y \le 7  \}\rightarrow \{ 0,1\}
$$

を考えます：

$$
 \boxed{
 \begin{matrix}
   0 &        0  &        0  &        0   &        0  &        0  &   0  \\ \\
   0 & \boxed{0} & \boxed{0} & \boxed{0}  & \boxed{0} & \boxed{0} &   0  \\ \\
   0 & \boxed{0} & \boxed{0} & \boxed{0}  & \boxed{0} & \boxed{0} &   0 \\ \\
   0 & \boxed{0} & \boxed{0} & \boxed{1}  & \boxed{0} & \boxed{0} &   0 \\ \\
   0 & \boxed{0} & \boxed{0} & \boxed{0}  & \boxed{0} & \boxed{0} &   0 \\ \\
   0 & \boxed{0} & \boxed{0} & \boxed{0}  & \boxed{0} & \boxed{0} &   0 \\ \\
   0 &        0  &        0  &        0   &        0  &        0  &   0
 \end{matrix}}.
$$

相関操作 $w(x,y) \star f(x,y)$ は出力を生成します。

$$
 \boxed{
 \begin{matrix}
 \boxed{0} & \boxed{0}  & \boxed{0} & \boxed{0} & \boxed{0} \\ \\
 \boxed{0} &  \boxed{9} & \boxed{8} & \boxed{7} & \boxed{0} \\ \\
 \boxed{0} &  \boxed{6} & \boxed{5} & \boxed{4} & \boxed{0} \\ \\
 \boxed{0} &  \boxed{3} & \boxed{2} & \boxed{1} & \boxed{0} \\ \\
 \boxed{0} & \boxed{0}  & \boxed{0} & \boxed{0} & \boxed{0}
 \end{matrix}},
$$

一方、畳み込み操作 $w(x,y) \ast f(x,y)$ は次のように生成します。

$$
 \boxed{
 \begin{matrix}
 \boxed{0} & \boxed{0} & \boxed{0} & \boxed{0} & \boxed{0} \\ \\
 \boxed{0} & \boxed{1} & \boxed{2} & \boxed{3} & \boxed{0}\\ \\
 \boxed{0} & \boxed{4} & \boxed{5} & \boxed{6} & \boxed{0} \\ \\
 \boxed{0} & \boxed{7} & \boxed{8} & \boxed{9} & \boxed{0} \\ \\
 \boxed{0} & \boxed{0} & \boxed{0} & \boxed{0} & \boxed{0}
 \end{matrix}}.
$$

## 離散畳み込みと相関を行列乗算として

離散畳み込みと相関操作は、入力の1つを [Toeplitz](https://en.wikipedia.org/wiki/Toeplitz_matrix) 行列に変換し、他方を列ベクトルとして表現することで、行列乗算としても定式化できます。たとえば、関数 $f:\{x \in \mathbb{N} \mid 1 \le x \le M \} \rightarrow \mathbb{R}$ とフィルタ $w: \{s \in \mathbb{N} \mid  -k_1 \le s \le k_1  \} \rightarrow \mathbb{R}$ を考えます。次の行列乗算は

$$
\begin{bmatrix}
w(-k_1) 	&  0	    & \ldots	& 0		   & 0			\\
\vdots 	& w(-k_1) 	& \ldots	& \vdots  & 0	        \\
w(k_1) 	    & \vdots   & \ldots	& 0		   & \vdots    \\
0 	    	& w(k_1)	& \ldots   & w(-k_1)  & 0		    \\
0 	        & 0		    & \ldots	& \vdots  & w(-k_1)	\\
\vdots     & \vdots	& \ldots	& w(k_1)   & \vdots	\\
0           & 0         & 0			& 0		   & w(k_1)
\end{bmatrix}
\begin{bmatrix}
f(1) \\
f(2) \\
f(3) \\
\vdots \\
f(M)
\end{bmatrix}
$$

は、$f(x)$ の境界がゼロでパディングされていると仮定した場合、畳み込み $w(s) \ast f(x)$ に相当します。

多次元畳み込みを行列乗算として表現するには、多次元配列を列ベクトルに変形し、同様の方法で進めます。もちろん、行列乗算の結果は適切な多次元配列に再形成する必要があります。

# オプション

以下のサブセクションでは、関数引数の有効なオプションについて詳しく説明します。

## `r` の選択肢

[ComputationalResources](https://github.com/timholy/ComputationalResources.jl) パッケージで定義されたリソース `r` を渡すことで、異なる実装にディスパッチできます。たとえば、

```julia
    imfilter(ArrayFireLibs(), img, kernel)
```

は、ArrayFire ライブラリを使用して GPU で計算を実行するよう要求します。

## `T` の選択肢

オプションとして、最初の引数として型 `T` を渡すことで出力画像の要素型を制御できます。

## `img` の選択肢

画像を定義する1次元、2次元または多次元配列を指定できます。

## `kernel` の選択肢

`kernel[0,0,..]` パラメータは、カーネルの原点（ゼロの変位）に対応します。`centered` を使用して原点を配列の中心に配置するか、OffsetArrays パッケージを使用して `kernel` のインデックスを手動で設定できます。たとえば、ランダムな *centered* 3x3 カーネルでフィルタリングするには、次のいずれかを使用できます。

```
kernel = centered(rand(3,3))
kernel = OffsetArray(rand(3,3), -1:1, -1:1)
```

`kernel` パラメータは、配列またはフィルタを適用する "因子化されたカーネル" のタプル `(filt1, filt2, ...)` として指定できます。この形式は、カーネルが分離可能であることがわかっている場合、処理を高速化できます。これらの各フィルタは、画像自体と同じ次元を持ち、フィルタリング軸を示す形状である必要があります。たとえば、最初の次元をフィルタリングするための3x1フィルタと、2次元をフィルタリングするための1x3フィルタです。2次元の場合、単一の行列として渡されたカーネルは分離可能性がチェックされます。このチェックを省略したい場合は、カーネルを単一要素のタプル `(kernel,)` として渡します。

## `border` の選択肢

画像の端では、`border` は画像を元の境界を超えて外挿するために使用されるパディングを指定します。各オプションの結果を示すために、6ピクセルの行からなる画像をアルファベット順に指定した例を示します：$\boxed{a \, b \, c \, d \, e \, f}$。左端と右端のパディングの効果のみを示しますが、上端と下端のパディングにも類似の結果が適用されます。

### `"replicate"` (デフォルト)

境界を超えた境界ピクセルが拡張されます。

$$
\boxed{
\begin{array}{l|c|r}
  a\, a\, a\, a  &  a \, b \, c \, d \, e \, f & f \, f \, f \, f
\end{array}
}
$$

参照： [`Pad`](@ref), [`padarray`](@ref), [`Inner`](@ref), [`NA`](@ref)  および [`NoPad`](@ref)

### `"circular"`

境界ピクセルがラップします。たとえば、左端を超えてインデックスすると、右端から値が返されます。

$$
\boxed{
\begin{array}{l|c|r}
  c\, d\, e\, f  &  a \, b \, c \, d \, e \, f & a \, b \, c \, d
\end{array}
}
$$

参照： [`Pad`](@ref), [`padarray`](@ref), [`Inner`](@ref), [`NA`](@ref)  および [`NoPad`](@ref)

### `"reflect"`

境界ピクセルがピクセル間の位置に対して反射します。つまり、ミラーリング時に境界ピクセルは省略されます。

$$
\boxed{
\begin{array}{l|c|r}
  e\, d\, c\, b  &  a \, b \, c \, d \, e \, f & e \, d \, c \, b
\end{array}
}
$$

参照： [`Pad`](@ref), [`padarray`](@ref), [`Inner`](@ref), [`NA`](@ref)  および [`NoPad`](@ref)

### `"symmetric"`

境界ピクセルがエッジ自体に対して反射します。

$$
\boxed{
\begin{array}{l|c|r}
  d\, c\, b\, a  &  a \, b \, c \, d \, e \, f & f \, e \, d \, c
\end{array}
}
$$

参照： [`Pad`](@ref), [`padarray`](@ref), [`Inner`](@ref), [`NA`](@ref)  および [`NoPad`](@ref)

### `Fill(m)`

境界ピクセルが指定された値 $m$ で埋められます。

$$
\boxed{
\begin{array}{l|c|r}
  m\, m\, m\, m  &  a \, b \, c \, d \, e \, f & m \, m \, m \, m
\end{array}
}
$$

参照： [`Pad`](@ref), [`padarray`](@ref), [`Inner`](@ref), [`NA`](@ref)  および [`NoPad`](@ref)

### `Inner()`

フィルタリングでエッジを破棄し、結果の内部のみを返すことを示します。

参照： [`Pad`](@ref), [`padarray`](@ref), [`Inner`](@ref), [`NA`](@ref)  および [`NoPad`](@ref)

### `NA()`

"NA" (Not Available) 境界条件を使用してフィルタリングを選択します。これは、ぼかしフィルタなど、正の重みのみを持つフィルタに最も適しています。

参照： [`Pad`](@ref), [`padarray`](@ref), [`Inner`](@ref), [`NA`](@ref)  および [`NoPad`](@ref)

## `alg` の選択肢

`alg` パラメータを使用して特定のアルゴリズムを選択できます： `FIR()` (有限インパルス応答、すなわち従来のデジタルフィルタリング) または `FFT()` (フーリエベースのフィルタリング)。選択が指定されていない場合、画像とカーネルのサイズに基づいて良好なパフォーマンスを提供するように選択されます。あるいは、[`KernelFactors.IIRGaussian`](@ref) のようなカスタムフィルタタイプを使用することもできます。

# 例

以下のサブセクションでは、一般的な使用例を強調します。

## 畳み込みと相関

```julia

# 2次元離散単位インパルス関数を作成します。
f = fill(0,(9,9));
f[5,5] = 1;

# フィルタ係数マスクを指定し、マスクの中心を原点として設定します。
w = centered([1 2 3; 4 5 6 ; 7 8 9]);

#=
 `imfilter` のデフォルト操作は相関です。 `w` を反射させることで
 `f` と `w` の畳み込みを計算します。 `Fill(0,w)` は、`f` の境界を
 ゼロでパディングしたいことを示します。パディングの量は自動的に
 w の長さを考慮して決定されます。
=#
correlation = imfilter(f,w,Fill(0,w))
convolution = imfilter(f,reflect(w),Fill(0,w))

```

## その他の境界パディングオプション

```julia
# 例の関数値 f とフィルタ係数 w。
f = reshape(1.0:81.0,9,9)
w = centered(reshape(1.0:9.0,3,3))

# 適切な文字列を指定することで、パディングの種類を指定できます。
imfilter(f,w,"replicate")
imfilter(f,w,"circular")
imfilter(f,w,"symmetric")
imfilter(f,w,"reflect")

# また、Pad タイプを明示的に使用してパディングスタイルを指定できます。
imfilter(f,w,Pad(:replicate))
imfilter(f,w,Pad(:circular))
imfilter(f,w,Pad(:symmetric))
imfilter(f,w,Pad(:reflect))

# 特定の値でパディングしたい場合は、Fill タイプを使用します。
imfilter(f,w,Fill(0,w))
imfilter(f,w,Fill(1,w))
imfilter(f,w,Fill(-1,w))

#=
  パディングなしでフィルタリング操作が定義される f の内部サブ配列を
  取得したい場合は 'Inner()' を指定します。
=#
imfilter(f,w,Inner())
```

# 参考文献

1. R. C. Gonzalez と R. E. Woods. *Digital Image Processing (3rd Edition)*.  Upper Saddle River, NJ, USA: Prentice-Hall,  2006.

参照： [`imfilter!`](@ref), [`centered`](@ref), [`padarray`](@ref), [`Pad`](@ref), [`Fill`](@ref), [`Inner`](@ref), [`KernelFactors.IIRGaussian`](@ref).
