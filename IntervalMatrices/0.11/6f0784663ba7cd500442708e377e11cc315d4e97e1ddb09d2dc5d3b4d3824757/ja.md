```
quadratic_expansion(A::IntervalMatrix, α::Real, β::Real)
```

区間行列の二次展開 $αA + βA^2$ を区間算術を用いて計算します。

### 入力

  * `A` – 区間行列
  * `α` – 線形係数
  * `β` – 二次係数

### 出力

$$
B := αA + βA^2
$$

を囲む区間行列。

### アルゴリズム

これは[1, Section 6]のアルゴリズムの変種です。$A = (aᵢⱼ)$ および $B := αA + βA^2 = (bᵢⱼ)$ の場合、各 $bᵢⱼ$ を繰り返し表現を因数分解することによって計算するというアイデアです（したがって、*単一使用表現*という用語が使われます）。

まず、$i = j$ の場合を考えます。この場合、

$$
bⱼⱼ = β\sum_\{k, k ≠ j} a_{jk} a_{kj} + (α + βa_{jj}) a_{jj}.
$$

次に、$i ≠ j$ の場合を考えます。この場合、

$$
bᵢⱼ = β\sum_\{k, k ≠ i, k ≠ j} a_{ik} a_{kj} + (α + βa_{ii} + βa_{jj}) a_{ij}.
$$

[1] Kosheleva, Kreinovich, Mayer, Nguyen. Computing the cube of an interval matrix is NP-hard. SAC 2005. ```
