```
NLAT1()
```

`NLAT1` は [^Chattopadhyay] と [^Pathak] で紹介された T₁ 変換アルゴリズムを実装しています。T₁ アルゴリズムは、入力配列の要素を二乗し、すべての奇数行を対象とします。

$$
\tilde{r}_{i,j} =
\begin{cases}
    r_{i,j} \times r_{i,j}, & \text{if } j \text{ is odd}; \\
    r_{i,j}, & \text{if } j \text{ is even}.
\end{cases}
$$

# 例

```jldoctest
julia> nlat = NLAT1()
NLAT1()

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
  4
  3
 16
  5
 36
  7
 64
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
   1    4    9
   4    5    6
  49   64   81
  10   11   12
 169  196  225
  16   17   18
 361  400  441

```

[^Chattopadhyay]: Chattopadhyay, Ashesh, et al. "Data-driven prediction of a multi-scale Lorenz 96 chaotic system using a hierarchy of deep learning methods: Reservoir computing, ANN, and RNN-LSTM." (2019).

[^Pathak]: Pathak, Jaideep, et al. "Model-free prediction of large spatiotemporally chaotic systems from data: A reservoir computing approach." Physical review letters 120.2 (2018): 024102.
