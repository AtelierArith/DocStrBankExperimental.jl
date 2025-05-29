PlanarFlow関数は次のように定義されます

$$
f({\bf{x}}) = {\bf{x}} + {\bf{u}} \tanh({\bf{w}}^\top {\bf{x}} + b)
$$

入力および出力の次元は$D$です。ここで、${\bf{x}}\in \mathbb{R}^D$は関数の入力を表します。さらに、${\bf{u}}\in \mathbb{R}^D$、${\bf{w}}\in \mathbb{R}^D$、および$b\in\mathbb{R}$は関数のパラメータを表します。この関数は入力空間を収縮および拡張します。

この関数は以下で紹介されています：

Rezende, Danilo, and Shakir Mohamed. "Variational inference with normalizing flows." *International conference on machine learning.* PMLR, 2015.
