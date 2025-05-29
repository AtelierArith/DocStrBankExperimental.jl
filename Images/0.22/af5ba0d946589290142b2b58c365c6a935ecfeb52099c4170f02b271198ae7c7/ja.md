```
hist_equalised_img = clahe(img, nbins, xblocks = 8, yblocks = 8, clip = 3)

```

入力画像に対してコントラスト制限適応ヒストグラム均等化（CLAHE）を実行します。これは、通常のヒストグラム均等化とは異なり、適応的手法は画像の異なるセクションに対応するいくつかのヒストグラムを計算し、それを使用して画像の明るさの値を再分配します。したがって、画像の各領域における局所的なコントラストを改善し、エッジの定義を強化するのに適しています。

# 詳細

ヒストグラム均等化は、最初は単一チャネルのグレースケール画像のコントラストを改善するために考案されました。この手法は、画像内の強度の分布をできるだけ均一に変換します[1]。均一性の自然な正当化は、画像の強度レベルが強度スケール上で広範囲にわたる場合、画像のコントラストがより良くなるということです。必要な変換は、累積ヒストグラムに基づくマッピングであることがわかります–詳細については[histeq](@ref)を参照してください。

ヒストグラム均等化の自然な拡張は、コントラストの強化をグローバルではなくローカルに適用することです[2]。概念的には、プロセスは画像を長方形の領域のグリッドに分割し、各文脈領域のローカルCDFに基づいてヒストグラム均等化を適用することを含むと考えることができます。しかし、ピクセルがある文脈領域から別の文脈領域に移行する際の遷移を滑らかにするために、ピクセルのマッピングはその文脈領域のローカルCDFのみに基づいて行われるわけではありません。むしろ、ピクセルのマッピングは、その文脈領域のCDFと隣接する領域のCDFに基づくバイリニアブレンドです。

適応ヒストグラム均等化では、画像 $\mathbf{G}$ は $P \times Q$ の等サイズのサブマトリックスに分割されます。

$$
\mathbf{G} =  \begin{bmatrix}
\mathbf{G}_{11} & \mathbf{G}_{12} & \ldots & \mathbf{G}_{1C} \\
\mathbf{G}_{21} & \mathbf{G}_{22} & \ldots & \mathbf{G}_{2C} \\
\vdots & \vdots & \ldots & \vdots \\
\mathbf{G}_{R1} & \mathbf{G}_{R2} & \ldots & \mathbf{G}_{RC} \\
\end{bmatrix}.
$$

各サブマトリックス $\mathbf{G}_{rc}$ に対して、対応するCDFを計算します。これを $T_{rc}(G_{i,j})$ と表記します。バイリニア補間ステップで使用されるCDFを決定するために、関数を導入することが有用です。

$$
\Phi(\mathbf{G}_{rc}) = \left(  \phi_{rc},  \phi'_{rc}\right) \triangleq \left(\frac{rP}{2}, \frac{cQ}{2} \right)
$$

そして、シーケンス $\left(\phi_{11}, \phi_{21}, \ldots, \phi_{R1} \right)$ と $\left(\phi'_{11}, \phi'_{12}, \ldots, \phi'_{1C} \right)$ を形成します。与えられたピクセル $G_{i,j}(\omega)$ に対して、$r$ と $c$ の値は不等式の解によって暗黙的に定義されます。

$$
\phi_{r1} \le i \le \phi_{(r+1)1}  \quad \text{and}  \quad  \phi'_{1c} \le j \le \phi'_{1(c+1)}.
$$

$$
r
$$

と $c$ が適切に定義されると、必要なCDFは次のように与えられます。

$$
\begin{aligned}
T_1(v)  & \triangleq  T_{rc}(G_{i,j}) \\
T_2(v)  & \triangleq  T_{(r+1)c}(G_{i,j}) \\
T_3(v)  & \triangleq  T_{(r+1)(c+1)}(G_{i,j}) \\
T_4(v)  & \triangleq  T_{r(c+1)}(G_{i,j}).
\end{aligned}
$$

最後に、

$$
\begin{aligned}
t  & \triangleq  \frac{i - \phi_{r1}}{\phi_{(r+1)1} - \phi_{r1} } \\
u  & \triangleq  \frac{j - \phi'_{1c}}{\phi'_{1(c+1)} - \phi'_{1c} },
\end{aligned}
$$

画像内の位置 $(i,j)$ での強度 $v$ を強度 $v'$ にマッピングするバイリニア補間変換は次のように与えられます[3]

$$
v' \triangleq \bar{T}(v)  = (1-t) (1-u)T_1(G_{i,j}) + t(1-u)T_2(G_{i,j}) + tuT_3(G_{i,j}) +(1-t)uT_4(G_{i,j}).
$$

コントラスト強化の不幸な副作用は、特にコントラスト強化の大きさが非常に高い場合に、画像内のノイズレベルを増幅する傾向があることです。コントラスト強化の大きさは $T(\cdot)$ の勾配に関連しており、勾配は連続する入力強度が灰色レベルスペクトル全体にどの程度引き伸ばされるかを決定します。勾配の大きさを制限することによって、ノイズ増幅のレベルを減少させることができます。

$$
T(\cdot)
$$

の導関数は経験的密度 $\hat{f}_{G}$ であるため、任意の入力強度におけるマッピング関数の傾きは、その強度におけるヒストグラム $\hat{f}_{G}$ の高さに比例します。したがって、ローカルマッピング関数の傾きを制限することは、ヒストグラムの高さをクリッピングすることと同等です。クリッピングプロセスの実装の詳細については[2]を参照してください。

# オプション

この関数のパラメータに関するさまざまなオプションは、以下でより詳細に説明されています。

## `img` の選択肢

`clahe` 関数はさまざまな入力タイプを処理できます。返される画像は入力タイプに依存します。入力が `Image` の場合、結果の画像は同じタイプであり、同じプロパティを持ちます。

カラー画像の場合、入力は[YIQ](https://en.wikipedia.org/wiki/YIQ)タイプに変換され、Yチャネルが均等化されます。これはIおよびQチャネルと組み合わされ、結果の画像は入力と同じタイプに変換されます。

## `nbins` の選択肢

各ローカル領域のヒストグラムの総ビン数を指定できます。

## `xblocks` と `yblocks` の選択肢

`xblocks` と `yblocks` は、入力画像を各方向に分割するブロックの数を指定します。デフォルトでは、両方の値は8に設定されています。

## `clip` の選択肢

`clip` パラメータは、ヒストグラムがクリッピングされる値を指定します。デフォルト値は3です。`clip` を超える値を持つヒストグラムビンの余剰は、他のビンに再分配されます。

# 例

```julia

using Images, TestImages, ImageView

img =  testimage("mandril_gray")
imgeq = clahe(img,256, xblocks = 50, yblocks = 50)

imshow(img)
imshow(imgeq)
```

# 参考文献

1. R. C. Gonzalez と R. E. Woods. *Digital Image Processing (3rd Edition)*. Upper Saddle River, NJ, USA: Prentice-Hall, 2006.
2. S. M. Pizer, E. P. Amburn, J. D. Austin, R. Cromartie, A. Geselowitz, T. Greer, B. ter Haar Romeny, J. B. Zimmerman と K. Zuiderveld “Adaptive histogram equalization and its variations,” *Computer Vision, Graphics, and Image Processing*, vol. 38, no. 1, p. 99, Apr. 1987. [10.1016/S0734-189X(87)80186-X](https://doi.org/10.1016/s0734-189x(87)80156-1)
3. W. H. Press, S. A. Teukolsky, W. T. Vetterling, と B. P. Flannery. *Numerical Recipes: The Art of Scientific Computing (3rd Edition)*. New York, NY, USA: Cambridge University Press, 2007.

また、[histmatch](@ref)、[histeq](@ref)、[imhist](@ref) および [adjust_gamma](@ref) も参照してください。
