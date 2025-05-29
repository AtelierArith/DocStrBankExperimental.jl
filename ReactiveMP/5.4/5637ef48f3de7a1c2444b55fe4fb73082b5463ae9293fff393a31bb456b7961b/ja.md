加法結合層は、特定の構造に従った可逆関数 ${\bf{y}} = g({\bf{x}})$ を指定します（写像 $g: \mathbb{R}^2 \rightarrow \mathbb{R}^2$ の場合）：

$$
    \begin{align}
        y_1 &= x_1 \\
        y_2 &= x_2 + f(x_1)
    \end{align}
$$

ここで、$f(\cdot)$ は写像 $f: \mathbb{R} \rightarrow \mathbb{R}$ を持つ任意の関数を示します。この関数は任意に複雑に選択できます。非線形関数（ニューラルネットワーク）は、複雑な関係をモデル化するためによく選ばれます。モデルの定義から、可逆性は簡単に達成できます。

$$
    \begin{align}
        x_1 &= y_1 \\
        x_2 &= y_2 - f(y_1)
    \end{align}
$$

現在の実装では、写像 $g: \mathbb{R}^2 \rightarrow \mathbb{R}^2$ のみが許可されていますが、この層は任意の入力次元に対して一般化できます。

`AdditiveCouplingLayer(f <: AbstractCouplingFlow)` は関数 `f` を用いて層構造を作成します。

### 例

```julia
f = PlanarFlow()
layer = AdditiveCouplingLayer(f)
```

この層構造は以下で紹介されています：

Dinh, Laurent, David Krueger, and Yoshua Bengio. "Nice: Non-linear independent components estimation." *arXiv preprint* arXiv:1410.8516 (2014).
