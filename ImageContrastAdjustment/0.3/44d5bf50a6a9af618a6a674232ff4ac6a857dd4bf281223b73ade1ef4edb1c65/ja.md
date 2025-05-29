```
    AdaptiveEqualization <: AbstractHistogramAdjustmentAlgorithm
    AdaptiveEqualization(; nbins = 256, minval = 0, maxval = 1, rblocks = 8, cblocks = 8, clip = 0.1)

    adjust_histogram([T,] img, f::AdaptiveEqualization)
    adjust_histogram!([out,] img, f::AdaptiveEqualization)
```

入力画像に対してコントラスト制限適応ヒストグラム均等化（CLAHE）を実行します。これは、通常のヒストグラム均等化とは異なり、適応法は画像の異なるセクションに対応するいくつかのヒストグラムを計算し、それを使用して画像の明るさの値を再分配します。したがって、画像の各領域における局所的なコントラストを改善し、エッジの定義を強化するのに適しています。

# 詳細

ヒストグラム均等化は、最初は単一チャネルのグレースケール画像のコントラストを改善するために考案されました。この方法は、画像内の強度の分布をできるだけ均一に変換します[1]。均一性の自然な正当化は、画像の強度レベルが強度スケール上で広範囲にわたる場合、画像のコントラストがより良くなるということです。必要な変換は、累積ヒストグラムに基づくマッピングであることがわかります–詳細については[Equalization](@ref)を参照してください。

ヒストグラム均等化の自然な拡張は、コントラストの強化をグローバルではなくローカルに適用することです[2]。概念的には、プロセスは画像を長方形の領域のグリッドに分割し、各文脈領域のローカルCDFに基づいてヒストグラム均等化を適用することを含むと考えることができます。しかし、ピクセルがある文脈領域から別の文脈領域に移行する際の遷移を滑らかにするために、ピクセルのマッピングは必ずしもその文脈領域のローカルCDFのみに基づいて行われるわけではありません。むしろ、ピクセルのマッピングは、その文脈領域のCDFと、隣接する領域のCDFに基づいて補間される場合があります。

適応ヒストグラム均等化では、画像 $\mathbf{G}$ は $P \times Q$ の等サイズのサブマトリックスに分割されます。

$$
\mathbf{G} =  \begin{bmatrix}
\mathbf{G}_{11} & \mathbf{G}_{12} & \ldots & \mathbf{G}_{1C} \\
\mathbf{G}_{21} & \mathbf{G}_{22} & \ldots & \mathbf{G}_{2C} \\
\vdots & \vdots & \ldots & \vdots \\
\mathbf{G}_{R1} & \mathbf{G}_{R2} & \ldots & \mathbf{G}_{RC} \\
\end{bmatrix}.
$$

各サブマトリックス $\mathbf{G}_{rc}$ に対して、対応するCDFを計算し、これを $T_{rc}(G_{i,j})$ と表記します。最も一般的な場合、4つのCDFが必要です。

$$
\begin{aligned}
T_1(v)  & \triangleq  T_{rc}(G_{i,j}) \\
T_2(v)  & \triangleq  T_{(r+1)c}(G_{i,j}) \\
T_3(v)  & \triangleq  T_{(r+1)(c+1)}(G_{i,j}) \\
T_4(v)  & \triangleq  T_{r(c+1)}(G_{i,j}).
\end{aligned}
$$

補間ステップで使用される特定のCDFを決定するために、(i) 関数を導入することが有用です。

$$
\Phi(\mathbf{G}_{rc}) = \left(  \phi_{rc},  \phi'_{rc}\right) \triangleq \left(rP - \frac{P}{2}, cQ - \frac{Q}{2} \right),
$$

(ii) シーケンス $\left(\phi_{11}, \phi_{21}, \ldots, \phi_{R1} \right)$ と $\left(\phi'_{11}, \phi'_{12}, \ldots, \phi'_{1C} \right)$ を形成し、(iii) 定義します。

$$
\begin{aligned}
t  & \triangleq  \frac{i - \phi_{r1}}{\phi_{(r+1)1} - \phi_{r1} } \\
u  & \triangleq  \frac{j - \phi'_{1c}}{\phi'_{1(c+1)} - \phi'_{1c} }.
\end{aligned}
$$

#### ケース I (内部)

範囲内のピクセル $G_{i,j}$ に対して

$$
P - \frac{P}{2} \le i \le RP - \frac{P}{2}  \quad \text{および}  \quad  Q - \frac{Q}{2} \le j \le CQ - \frac{Q}{2}.
$$

$$
r
$$

と $c$ の値は、不等式の解によって暗黙的に定義されます。

$$
\phi_{r1} \le i < \phi_{(r+1)1}  \quad \text{および}  \quad  \phi'_{1c} \le j < \phi'_{1(c+1)}.
$$

*バイリニア補間*変換は、画像内の位置 $(i,j)$ での強度 $v$ を強度 $v'$ にマッピングします。

$$
v' \triangleq \bar{T}(v)  = (1-t) (1-u)T_1(G_{i,j}) + t(1-u)T_2(G_{i,j}) + tuT_3(G_{i,j}) +(1-t)uT_4(G_{i,j}).
$$

#### ケース II (垂直ボーダー)

範囲内のピクセル $G_{i,j}$ に対して

$$
P - \frac{P}{2} \le i \le RP - \frac{P}{2}  \quad \text{および}  \quad  1 \le j < Q - \frac{Q}{2}  \; \cup \;   CQ - \frac{Q}{2} < j \le CQ,
$$

$$
r
$$

は不等式 $\phi_{r1} \le i < \phi_{(r+1)1}$ の解によって暗黙的に定義されますが、

$$
c = \begin{cases}
   1, & \text{もし }  \quad  1 \le j < Q - \frac{Q}{2}  \\
   C, & \text{もし } \quad   CQ - \frac{Q}{2} < j \le CQ.
\end{cases}
$$

*線形補間*変換は、画像内の位置 $(i,j)$ での強度 $v$ を強度 $v'$ にマッピングします。

$$
v' \triangleq \bar{T}(v)  = (1-t)T_1(G_{i,j}) + tT_2(G_{i,j}).
$$

#### ケース III (水平ボーダー)

範囲内のピクセル $G_{i,j}$ に対して

$$
1 \le i < P - \frac{P}{2}  \;\cup \;   RP - \frac{P}{2} < i \le RP    \quad \text{および}  \quad  Q - \frac{Q}{2} \le j \le CQ - \frac{Q}{2},
$$

$$
c
$$

は不等式 $\phi'_{1c} \le j < \phi'_{1(c+1)}$ の解によって暗黙的に定義されますが、

$$
r = \begin{cases}
   1, & \text{もし }  \quad  1 \le i < P - \frac{P}{2}  \\
   R, & \text{もし } \quad   RP - \frac{P}{2} < i \le RP .
\end{cases}
$$

*線形補間*変換は、画像内の位置 $(i,j)$ での強度 $v$ を強度 $v'$ にマッピングします。

$$
v' \triangleq \bar{T}(v)  = (1-u)T_1(G_{i,j}) + uT_4(G_{i,j}).
$$

#### ケース IV (コーナー)

範囲内のピクセル $G_{i,j}$ に対して

$$
1 \le i < \frac{P}{2}  \;\cup \; RP - \frac{P}{2} < i \le RP   \quad \text{および}  \quad  1 \le j < CQ -  \frac{Q}{2} \; \cup \;   CQ - \frac{Q}{2} < j \le CQ ,
$$

次のようになります。

$$
r = \begin{cases}
   1, & \text{もし }  \quad  1 \le i < P - \frac{P}{2}  \\
   R, & \text{もし } \quad   RP - \frac{P}{2} < i \le RP
\end{cases}
 \quad \text{および}  \quad
c = \begin{cases}
   1, & \text{もし }  \quad  1 \le j < Q - \frac{Q}{2}  \\
   C, & \text{もし } \quad   CQ - \frac{Q}{2} < j \le CQ.
\end{cases}
$$

画像内の位置 $(i,j)$ での強度 $v$ を強度 $v'$ にマッピングする変換は次のようになります。

$$
v' \triangleq \bar{T}(v)  = T_1(G_{i,j}).
$$

## コントラストの制限

コントラストの強化の不幸な副作用は、特にコントラストの強化の大きさが非常に高い場合に、画像内のノイズレベルを増幅する傾向があることです。コントラストの強化の大きさは、$T(\cdot)$ の勾配に関連しており、勾配は連続する入力強度が灰色レベルスペクトル全体にどの程度引き伸ばされるかを決定します。コントラストの強化の大きさを制限することによって、ノイズの増幅レベルを減少させることができます。つまり、勾配の大きさを制限することによってです。

$$
T(\cdot)
$$

の導関数は経験的密度 $\hat{f}_{G}$ であるため、任意の入力強度におけるマッピング関数の傾きは、その強度におけるヒストグラム $\hat{f}_{G}$ の高さに比例します。したがって、ローカルマッピング関数の傾きを制限することは、ヒストグラムの高さをクリッピングすることと同等です。クリッピングプロセスの実装の詳細については[2]を参照してください。

# オプション

この関数のパラメータに関するさまざまなオプションが以下に詳述されています。

## `img` の選択肢

この関数はさまざまな入力タイプを処理できます。返される画像は入力タイプに依存します。

カラー画像の場合、入力は[YIQ](https://en.wikipedia.org/wiki/YIQ)タイプに変換され、Yチャネルが均等化されます。これはIおよびQチャネルと組み合わされ、結果の画像は入力と同じタイプに変換されます。

## `AdaptiveEqualization` における `nbins` の選択肢

各ローカル領域のヒストグラムの総ビン数を指定できます。

## `AdaptiveEqualization` における `rblocks` と `cblocks` の選択肢

`rblocks` と `cblocks` は、入力画像を各方向に分割するブロックの数を指定します。デフォルトでは、両方の値は8に設定されています。

## `AdaptiveEqualization` における `clip` の選択肢

`clip` パラメータは0と1の間の値でなければなりません。これは、ヒストグラムがクリッピングされる暗黙の閾値を定義します。閾値を超えるカウントは、できるだけ均等に再分配され、どのビンも閾値制限を超えないようにします。ゼロの値はクリッピングなしを意味し、1の値は最小の実行可能なビン制限で閾値を設定します。ビン制限は、すべてのビンカウントが再分配され、どのビンカウントも制限を超えない場合に実行可能です。実際には、`clip` の値がゼロの場合は最大のコントラスト強化に対応し、`clip` の値が1の場合は最小のコントラスト強化に対応します。デフォルト値は `0.1` です。

## `AdaptiveEqualization` における `minval` と `maxval` の選択肢

`minval` と `maxval` が指定されている場合、強度は範囲 [`minval`, `maxval`] に均等化されます。デフォルト値は0と1です。

# 例

```julia

using TestImages, FileIO, ImageView

img =  testimage("mandril_gray")
imgeq = adjust_histogram(img, AdaptiveEqualization(nbins = 256, rblocks = 4, cblocks = 4, clip = 0.2))

imshow(img)
imshow(imgeq)
```

# 参考文献

1. R. C. Gonzalez と R. E. Woods. *Digital Image Processing (3rd Edition)*. Upper Saddle River, NJ, USA: Prentice-Hall, 2006.
2. S. M. Pizer, E. P. Amburn, J. D. Austin, R. Cromartie, A. Geselowitz, T. Greer, B. ter Haar Romeny, J. B. Zimmerman と K. Zuiderveld “Adaptive histogram equalization and its variations,” *Computer Vision, Graphics, and Image Processing*, vol. 38, no. 1, p. 99, Apr. 1987. [10.1016/S0734-189X(87)80186-X](https://doi.org/10.1016/s0734-189x(87)80156-1)
3. W. H. Press, S. A. Teukolsky, W. T. Vetterling, と B. P. Flannery.  *Numerical Recipes: The Art of Scientific Computing (3rd Edition)*. New York, NY, USA: Cambridge University Press, 2007.

```
