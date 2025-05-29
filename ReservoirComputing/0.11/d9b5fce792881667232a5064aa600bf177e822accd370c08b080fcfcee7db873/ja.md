```
NLAT3()
```

T₃変換アルゴリズムを実装します。これは、[^\Chattopadhyay]に詳述されています。このアルゴリズムは、各奇数インデックスの行（2行目から始まる）を、直前の行と直後の行の積で乗算することによって、貯水池の状態を修正します。

$$
\tilde{r}_{i,j} =
\begin{cases}
r_{i,j-1} \times r_{i,j+1}, & \text{if } j > 1 \text{ is odd}; \\
r_{i,j}, & \text{if } j = 1 \text{ or even.}
\end{cases}
$$

# 例

```jldoctest
julia> nlat = NLAT3()
NLAT3()

julia> x_old = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
10-element Vector{Int64}:
 0
 1
 2
 3
 4
 5
 6
 7
 8
 9

julia> n_new = nlat(x_old)
10-element Vector{Int64}:
  0
  1
  3
  3
 15
  5
 35
  7
 63
  9

julia> mat_old = [1  2  3;
                   4  5  6;
                   7  8  9;
                  10 11 12;
                  13 14 15;
                  16 17 18;
                  19 20 21]
7×3 Matrix{Int64}:
  1   2   3
  4   5   6
  7   8   9
 10  11  12
 13  14  15
 16  17  18
 19  20  21

julia> mat_new = nlat(mat_old)
7×3 Matrix{Int64}:
   1    2    3
   4    5    6
  40   55   72
  10   11   12
 160  187  216
  16   17   18
  19   20   21

```

[^Chattopadhyay]: Chattopadhyay, Ashesh, et al. "データ駆動型の多スケールLorenz 96カオスシステムの機械学習手法を用いた予測：貯水池コンピューティング、人工ニューラルネットワーク、長短期記憶ネットワーク。" (2019).
