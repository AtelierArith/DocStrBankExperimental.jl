```
cayley(B̄::StiefelLieAlgHorMatrix)
```

`B`のケイリー再tractionを計算します。

# 実装

内部的には次のように使用されています。

$$
\mathrm{Cayley}(\bar{B}) = \mathbb{I} + \frac{1}{2} B' (\mathbb{I}_{2n} - \frac{1}{2} (B'')^T B')^{-1} (B'')^T (\mathbb{I} + \frac{1}{2} B),
$$

ここで

$$
\bar{B} = \begin{bmatrix}
    A & -B^T \\ 
    B & \mathbb{O}
\end{bmatrix} = \begin{bmatrix}  \frac{1}{2}A & \mathbb{I} \\ B & \mathbb{O} \end{bmatrix} \begin{bmatrix}  \mathbb{I} & \mathbb{O} \\ \frac{1}{2}A & -B^T  \end{bmatrix} =: B'(B'')^T,
$$

すなわち、$\bar{B}$は2つの$N\times{}2n$行列の積として表現されます。
