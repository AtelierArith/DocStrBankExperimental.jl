```
map_qubo(J::AbstractMatrix, h::AbstractVector) -> QUBOResult
```

QUBO問題を欠陥のあるキンググラフ上の重み付きMIS問題にマッピングします。QUBO問題は以下のハミルトニアンによって定義されます。

$$
E(z) = -\sum_{i<j} J_{ij} z_i z_j + \sum_i h_i z_i
$$

!!! note
    入力結合強度とオンサイトエネルギーは << 1 でなければなりません。


QUBOガジェットは次のようになります。

```
⋅ ⋅ ● ⋅
● A B ⋅
⋅ C D ●
⋅ ● ⋅ ⋅
```

ここで `A`、`B`、`C`、`D` は次のように定義されるノードの重みです。

$$
\begin{align}
A = -J_{ij} + 4\\
B = J_{ij} + 4\\
C = J_{ij} + 4\\
D = -J_{ij} + 4
\end{align}
$$

残りのノード `●` の重みは 2 です（境界ノードの重みは $1 - h_i$ です）。
