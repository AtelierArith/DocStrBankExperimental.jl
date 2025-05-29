```julia
    padarray([T], img, border) --> imgpadded
```

配列 `img` と境界条件および追加するパディングの量を指定する `border` からパディングされた画像を生成します。

# 出力

入力画像の拡張であり、追加のピクセルは `border` で指定された外挿スキームを使用して入力画像の境界から導出されます。

# 詳細

この関数は、1次元、2次元、または多次元の画像をサポートします。出力画像の要素型 `T` を指定できます。

## オプション

有効な `border` オプションは以下に説明されています。

### `Pad`

タイプ `Pad` は、画像の境界を超えてピクセルを外挿するために使用されるパディングの形式を指定します。インスタンスは、画像の境界条件を指定するシンボル `style` を設定する必要があります。

シンボルは以下のいずれかでなければなりません：

  * `:replicate`（エッジの値を無限に繰り返す）、
  * `:circular`（画像のエッジが「巻きつく」）、
  * `:symmetric`（画像がピクセル間の位置に対して反射する）、
  * `:reflect`（画像がエッジ自体に対して反射する）。

各オプションの詳細と例については、[`Pad`](@ref) のドキュメントを参照してください。

### `Fill`

タイプ `Fill` は、画像の境界を超えてピクセルを外挿するために使用される特定の値を指定します。詳細と図については、[`Fill`](@ref) のドキュメントを参照してください。

# 2Dの例

各例は入力配列に基づいています

$$
\mathbf{A} =
\boxed{
\begin{matrix}
 1  & 2  &  3  &  4 & 5  & 6 \\
 2  & 4  &  6  &  8 & 10 & 12 \\
 3  & 6  &  9  & 12 & 15 & 18 \\
 4  & 8  & 12  & 16 & 20 & 24 \\
 5  & 10 & 15  & 20 & 25 & 30 \\
 6  & 12 & 18  & 24 & 30 & 36
 \end{matrix}}.
$$

## `Pad` を使用した例

コマンド `padarray(A, Pad(:replicate,4,4))` は次のようになります

$$
\boxed{
\begin{array}{ccccccccccccc}
1 & 1 & 1 & 1 &         1   &          2   &          3   &          4   &          5   &          6   &  6  &  6  &  6  &  6 \\
1 & 1 & 1 & 1 &         1   &          2   &          3   &          4   &          5   &          6   &  6  &  6  &  6  &  6 \\
1 & 1 & 1 & 1 &         1   &          2   &          3   &          4   &          5   &          6   &  6  &  6  &  6  &  6 \\
1 & 1 & 1 & 1 &         1   &          2   &          3   &          4   &          5   &          6   &  6  &  6  &  6  &  6 \\
1 & 1 & 1 & 1 &  \boxed{1}  &   \boxed{2}  &   \boxed{3}  &   \boxed{4}  &   \boxed{5}  &   \boxed{6}  &  6  &  6  &  6  &  6 \\
2 & 2 & 2 & 2 &  \boxed{2}  &   \boxed{4}  &   \boxed{6}  &   \boxed{8}  &  \boxed{10}  &  \boxed{12}  & 12  & 12  & 12  & 12 \\
3 & 3 & 3 & 3 &  \boxed{3}  &   \boxed{6}  &   \boxed{9}  &  \boxed{12}  &  \boxed{15}  &  \boxed{18}  & 18  & 18  & 18  & 18 \\
4 & 4 & 4 & 4 &  \boxed{4}  &   \boxed{8}  &  \boxed{12}  &  \boxed{16}  &  \boxed{20}  &  \boxed{24}  & 24  & 24  & 24  & 24 \\
5 & 5 & 5 & 5 &  \boxed{5}  &  \boxed{10}  &  \boxed{15}  &  \boxed{20}  &  \boxed{25}  &  \boxed{30}  & 30  & 30  & 30  & 30 \\
6 & 6 & 6 & 6 &  \boxed{6}  &  \boxed{12}  &  \boxed{18}  &  \boxed{24}  &  \boxed{30}  &  \boxed{36}  & 36  & 36  & 36  & 36 \\
6 & 6 & 6 & 6 &         6   &         12   &         18   &         24   &         30   &         36   & 36  & 36  & 36  & 36 \\
6 & 6 & 6 & 6 &         6   &         12   &         18   &         24   &         30   &         36   & 36  & 36  & 36  & 36 \\
6 & 6 & 6 & 6 &         6   &         12   &         18   &         24   &         30   &         36   & 36  & 36  & 36  & 36 \\
6 & 6 & 6 & 6 &         6   &         12   &         18   &         24   &         30   &         36   & 36  & 36  & 36  & 36
 \end{array}
}.
$$

コマンド `padarray(A, Pad(:circular,4,4))` は次のようになります

$$
\boxed{
\begin{array}{ccccccccccccc}
9  & 12 & 15 & 18 &         3  &         6   &         9   &         12  &          15  &         18  & 3 &  6 &  9 & 12 \\
12 & 16 & 20 & 24 &         4  &         8   &        12   &         16  &          20  &         24  & 4 &  8 & 12 & 16 \\
15 & 20 & 25 & 30 &         5  &        10   &        15   &         20  &          25  &         30  & 5 & 10 & 15 & 20 \\
18 & 24 & 30 & 36 &         6  &        12   &        18   &         24  &          30  &         36  & 6 & 12 & 18 & 24 \\
3  &  4 &  5 &  6 &  \boxed{1} &  \boxed{2}  &  \boxed{3}  &  \boxed{4}  &  \boxed{5}   &  \boxed{6}  & 1 &  2 &  3 &  4 \\
6  &  8 & 10 & 12 &  \boxed{2} &  \boxed{4}  &  \boxed{6}  &  \boxed{8}  &  \boxed{10}  &  \boxed{12} & 2 &  4 &  6 &  8 \\
9  & 12 & 15 & 18 &  \boxed{3} &  \boxed{6}  &  \boxed{9}  &  \boxed{12} &  \boxed{15}  &  \boxed{18} & 3 &  6 &  9 & 12 \\
12 & 16 & 20 & 24 &  \boxed{4} &  \boxed{8}  &  \boxed{12} &  \boxed{16} &  \boxed{20}  &  \boxed{24} & 4 &  8 & 12 & 16 \\
15 & 20 & 25 & 30 &  \boxed{5} &  \boxed{10} &  \boxed{15} &  \boxed{20} &  \boxed{25}  &  \boxed{30} & 5 & 10 & 15 & 20 \\
18 & 24 & 30 & 36 &  \boxed{6} &  \boxed{12} &  \boxed{18} &  \boxed{24} &  \boxed{30}  &  \boxed{36} & 6 & 12 & 18 & 24 \\
3  &  4 &  5 &  6 &         1  &          2  &          3  &          4  &           5  &          6  & 1 &  2 &  3 &  4 \\
6  &  8 & 10 & 12 &         2  &          4  &          6  &          8  &          10  &         12  & 2 &  4 &  6 &  8 \\
9  & 12 & 15 & 18 &         3  &          6  &          9  &         12  &          15  &         18  & 3 &  6 &  9 & 12 \\
12 & 16 & 20 & 24 &         4  &          8  &         12  &         16  &          20  &         24  & 4 &  8 & 12 & 16
\end{array}
}.
$$

コマンド `padarray(A, Pad(:symmetric,4,4))` は次のようになります

$$
\boxed{
\begin{array}{ccccccccccccc}
16 & 12 &  8 & 4 &         4  &          8  &         12  &          16 &          20 &         24  & 24 & 20 & 16 & 12 \\
12 &  9 &  6 & 3 &         3  &          6  &         9   &          12 &          15 &         18  & 18 & 15 & 12 &  9 \\
 8 &  6 &  4 & 2 &         2  &          4  &         6   &          8  &          10 &         12  & 12 & 10 &  8 &  6 \\
 4 &  3 &  2 & 1 &         1  &          2  &         3   &          4  &          5  &         6   &  6 &  5 &  4 &  3 \\
 4 &  3 &  2 & 1 &  \boxed{1} &   \boxed{2} &  \boxed{3}  &   \boxed{4} &  \boxed{5}  &  \boxed{6}  &  6 &  5 &  4 &  3 \\
 8 &  6 &  4 & 2 &  \boxed{2} &   \boxed{4} &  \boxed{6}  &   \boxed{8} &  \boxed{10} &  \boxed{12} & 12 & 10 &  8 &  6 \\
12 &  9 &  6 & 3 &  \boxed{3} &   \boxed{6} &  \boxed{9}  &  \boxed{12} &  \boxed{15} &  \boxed{18} & 18 & 15 & 12 &  9 \\
16 & 12 &  8 & 4 &  \boxed{4} &   \boxed{8} &  \boxed{12} &  \boxed{16} &  \boxed{20} &  \boxed{24} & 24 & 20 & 16 & 12 \\
20 & 15 & 10 & 5 &  \boxed{5} &  \boxed{10} &  \boxed{15} &  \boxed{20} &  \boxed{25} &  \boxed{30} & 30 & 25 & 20 & 15 \\
24 & 18 & 12 & 6 &  \boxed{6} &  \boxed{12} &  \boxed{18} &  \boxed{24} &  \boxed{30} &  \boxed{36} & 36 & 30 & 24 & 18 \\
24 & 18 & 12 & 6 &         6  &         12  &         18  &         24  &         30  &         36  & 36 & 30 & 24 & 18 \\
20 & 15 & 10 & 5 &         5  &         10  &         15  &         20  &         25  &         30  & 30 & 25 & 20 & 15 \\
16 & 12 &  8 & 4 &         4  &          8  &         12  &         16  &         20  &         24  & 24 & 20 & 16 & 12 \\
12 &  9 &  6 & 3 &         3  &          6  &          9  &         12  &         15  &         18  & 18 & 15 & 12 &  9
\end{array}
}.
$$

コマンド `padarray(A, Pad(:reflect,4,4))` は次のようになります

$$
\boxed{
\begin{array}{ccccccccccccc}
25 & 20 & 15 & 10 &         5  &         10  &         15   &         20  &          25  &         30  & 25 & 20 & 15 & 10 \\
20 & 16 & 12 &  8 &         4  &         8   &         12   &         16  &          20  &         24  & 20 & 16 & 12 &  8 \\
15 & 12 &  9 &  6 &         3  &         6   &          9   &         12  &          15  &         18  & 15 & 12 &  9 &  6 \\
10 &  8 &  6 &  4 &         2  &         4   &          6   &         8   &          10  &         12  & 10 &  8 &  6 &  4 \\
5  &  4 &  3 &  2 &  \boxed{1} &  \boxed{2}  &   \boxed{3}  &  \boxed{4}  &   \boxed{5}  &  \boxed{6}  &  5 &  4 &  3 &  2 \\
10 &  8 &  6 &  4 &  \boxed{2} &  \boxed{4}  &   \boxed{6}  &  \boxed{8}  &   \boxed{10} &  \boxed{12} & 10 &  8 &  6 &  4 \\
15 & 12 &  9 &  6 &  \boxed{3} &  \boxed{6}  &   \boxed{9}  &  \boxed{12} &   \boxed{15} &  \boxed{18} & 15 & 12 &  9 &  6 \\
20 & 16 & 12 &  8 &  \boxed{4} &  \boxed{8}  &   \boxed{12} &  \boxed{16} &   \boxed{20} &  \boxed{24} & 20 & 16 & 12 &  8 \\
25 & 20 & 15 & 10 &  \boxed{5} &  \boxed{10} &   \boxed{15} &  \boxed{20} &   \boxed{25} &  \boxed{30} & 25 & 20 & 15 & 10 \\
30 & 24 & 18 & 12 &  \boxed{6} &  \boxed{12} &   \boxed{18} &  \boxed{24} &   \boxed{30} &  \boxed{36} & 30 & 24 & 18 & 12 \\
25 & 20 & 15 & 10 &         5  &         10  &          15  &         20  &          25  &         30  & 25 & 20 & 15 & 10 \\
20 & 16 & 12 &  8 &         4  &         8   &          12  &         16  &          20  &         24  & 20 & 16 & 12 &  8 \\
15 & 12 &  9 &  6 &         3  &         6   &           9  &         12  &          15  &         18  & 15 & 12 &  9 &  6 \\
10 &  8 &  6 &  4 &         2  &         4   &           6  &          8  &          10  &         12  & 10 &  8 &  6 &  4
\end{array}
}.
$$

## `Fill` を使用した例

コマンド `padarray(A, Fill(0,(4,4),(4,4)))` は次のようになります

$$
\boxed{
\begin{array}{ccccccccccccc}
0 & 0 & 0 & 0 &         0  &         0   &         0   &         0   &         0   &          0   & 0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 &         0  &         0   &         0   &         0   &         0   &          0   & 0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 &         0  &         0   &         0   &         0   &         0   &          0   & 0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 &         0  &         0   &         0   &         0   &         0   &          0   & 0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 &  \boxed{1} &  \boxed{2}  &  \boxed{3}  &  \boxed{4}  &  \boxed{5}  &   \boxed{6}  & 0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 &  \boxed{2} &  \boxed{4}  &  \boxed{6}  &  \boxed{8}  &  \boxed{10} &   \boxed{12} & 0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 &  \boxed{3} &  \boxed{6}  &  \boxed{9}  &  \boxed{12} &  \boxed{15} &   \boxed{18} & 0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 &  \boxed{4} &  \boxed{8}  &  \boxed{12} &  \boxed{16} &  \boxed{20} &   \boxed{24} & 0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 &  \boxed{5} &  \boxed{10} &  \boxed{15} &  \boxed{20} &  \boxed{25} &   \boxed{30} & 0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 &  \boxed{6} &  \boxed{12} &  \boxed{18} &  \boxed{24} &  \boxed{30} &   \boxed{36} & 0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 &         0  &         0   &         0   &         0   &         0   &          0   & 0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 &         0  &         0   &         0   &         0   &         0   &          0   & 0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 &         0  &         0   &         0   &         0   &         0   &          0   & 0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 &         0  &         0   &         0   &         0   &         0   &          0   & 0 & 0 & 0 & 0
\end{array}
}.
$$

# 3Dの例

各例は次の多次元配列 $\mathsf{A} \in\mathbb{R}^{2 \times 2 \times 2}$ に基づいています

$$
\mathsf{A}(:,:,1) =
\boxed{
\begin{array}{cc}
1 & 2 \\
3 & 4
\end{array}}
\quad
\text{および}
\quad
\mathsf{A}(:,:,2) =
\boxed{
\begin{array}{cc}
5 & 6 \\
7 & 8
\end{array}}.
$$

各例は新しい多次元配列 $\mathsf{A}' \in \mathbb{R}^{4 \times 4 \times 4}$ を生成します。タイプは `OffsetArray` であり、追加された次元は負またはゼロから始まる場合があります。

## `Pad` を使用した例

コマンド `padarray(A,Pad(:replicate,1,1,1))` は次のようになります

$$
\begin{aligned}
\mathsf{A}'(:,:,0) & =
\boxed{
\begin{array}{cccc}
1 & 1 & 2 & 2 \\
1 & 1 & 2 & 2 \\
3 & 3 & 4 & 4 \\
3 & 3 & 4 & 4
\end{array}}
&
\mathsf{A}'(:,:,1) & =
\boxed{
\begin{array}{cccc}
1 &         1  &         2  & 2 \\
1 &  \boxed{1} &  \boxed{2} & 2 \\
3 &  \boxed{3} &  \boxed{4} & 4 \\
3 &         3  &         4  & 4
\end{array}} \\
\mathsf{A}'(:,:,2) & =
\boxed{
\begin{array}{cccc}
5 &         5  &         6  & 6 \\
5 &  \boxed{5} &  \boxed{6} & 6 \\
7 &  \boxed{7} &  \boxed{8} & 8 \\
7 &         7  &         8  & 8
\end{array}}
&
\mathsf{A}'(:,:,3) & =
\boxed{
\begin{array}{cccc}
5 & 5 & 6 & 6 \\
5 & 5 & 6 & 6 \\
7 & 7 & 8 & 8 \\
7 & 7 & 8 & 8
\end{array}}
\end{aligned}
.
$$

コマンド `padarray(A,Pad(:circular,1,1,1))` は次のようになります

$$
\begin{aligned}
\mathsf{A}'(:,:,0) & =
\boxed{
\begin{array}{cccc}
8 & 7 & 8 & 7 \\
6 & 5 & 6 & 5 \\
8 & 7 & 8 & 7 \\
6 & 5 & 6 & 5
\end{array}}
&
\mathsf{A}'(:,:,1) & =
\boxed{
\begin{array}{cccc}
4 &         3  &         4  & 3 \\
2 &  \boxed{1} &  \boxed{2} & 1 \\
4 &  \boxed{3} &  \boxed{4} & 3 \\
2 &         1  &         2  & 1
\end{array}} \\
\mathsf{A}'(:,:,2) & =
\boxed{
\begin{array}{cccc}
8 &         7  &         8  & 7 \\
6 &  \boxed{5} &  \boxed{6} & 5 \\
8 &  \boxed{7} &  \boxed{8} & 7 \\
6 &         5  &         6  & 5
\end{array}}
&
\mathsf{A}'(:,:,3) & =
\boxed{
\begin{array}{cccc}
4 & 3 & 4 & 3 \\
2 & 1 & 2 & 1 \\
4 & 3 & 4 & 3 \\
2 & 1 & 2 & 1
\end{array}}
\end{aligned}
.
$$

コマンド `padarray(A,Pad(:symmetric,1,1,1))` は次のようになります

$$
\begin{aligned}
\mathsf{A}'(:,:,0) & =
\boxed{
\begin{array}{cccc}
1 & 1 & 2 & 2 \\
1 & 1 & 2 & 2 \\
3 & 3 & 4 & 4 \\
3 & 3 & 4 & 4
\end{array}}
&
\mathsf{A}'(:,:,1) & =
\boxed{
\begin{array}{cccc}
1 &         1  &         2  & 2 \\
1 &  \boxed{1} &  \boxed{2} & 2 \\
2 &  \boxed{3} &  \boxed{4} & 4 \\
2 &         3  &         4  & 4
\end{array}} \\
\mathsf{A}'(:,:,2) & =
\boxed{
\begin{array}{cccc}
5 &         5  &         6  & 6 \\
5 &  \boxed{5} &  \boxed{6} & 6 \\
7 &  \boxed{7} &  \boxed{8} & 8 \\
7 &         7  &         8  & 8
\end{array}}
&
\mathsf{A}'(:,:,3) & =
\boxed{
\begin{array}{cccc}
5 & 5 & 6 & 6 \\
5 & 5 & 6 & 6 \\
7 & 7 & 8 & 8 \\
7 & 7 & 8 & 8
\end{array}}
\end{aligned}
.
$$

コマンド `padarray(A,Pad(:reflect,1,1,1))` は次のようになります

$$
\begin{aligned}
\mathsf{A}'(:,:,0) & =
\boxed{
\begin{array}{cccc}
8 & 7 & 8 & 7 \\
6 & 5 & 6 & 5 \\
8 & 7 & 8 & 7 \\
6 & 5 & 6 & 5
\end{array}}
&
\mathsf{A}'(:,:,1) & =
\boxed{
\begin{array}{cccc}
4 &         3  &         4  & 3 \\
2 &  \boxed{1} &  \boxed{2} & 1 \\
4 &  \boxed{3} &  \boxed{4} & 3 \\
2 &         1  &         2  & 1
\end{array}} \\
\mathsf{A}'(:,:,2) & =
\boxed{
\begin{array}{cccc}
8 &         7  &         8  & 7 \\
6 &  \boxed{5} &  \boxed{6} & 5 \\
8 &  \boxed{7} &  \boxed{8} & 7 \\
6 &         5  &         6  & 5
\end{array}}
&
\mathsf{A}'(:,:,3) & =
\boxed{
\begin{array}{cccc}
4 & 3 & 4 & 3 \\
2 & 1 & 2 & 1 \\
4 & 3 & 4 & 3 \\
2 & 1 & 2 & 1
\end{array}}
\end{aligned}
.
$$

## `Fill` を使用した例

コマンド `padarray(A,Fill(0,(1,1,1)))` は次のようになります

$$
\begin{aligned}
\mathsf{A}'(:,:,0) & =
\boxed{
\begin{array}{cccc}
0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0
\end{array}}
&
\mathsf{A}'(:,:,1) & =
\boxed{
\begin{array}{cccc}
0 &         0  &         0  & 0 \\
0 &  \boxed{1} &  \boxed{2} & 0 \\
0 &  \boxed{3} &  \boxed{4} & 0 \\
0 &         0  &         0  & 0
\end{array}} \\
\mathsf{A}'(:,:,2) & =
\boxed{
\begin{array}{cccc}
0 &         0  &         0  & 0 \\
0 &  \boxed{5} &  \boxed{6} & 0 \\
0 &  \boxed{7} &  \boxed{8} & 0 \\
0 &         0  &         0  & 0
\end{array}}
&
\mathsf{A}'(:,:,3) & =
\boxed{
\begin{array}{cccc}
0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0
\end{array}}
\end{aligned}
.
$$

---
