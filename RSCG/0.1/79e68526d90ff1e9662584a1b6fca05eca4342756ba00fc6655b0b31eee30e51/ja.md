````
greensfunctions_col(j::Integer,σ::Array{ComplexF64,1},A)

グリーン関数 G とベクトル b の積を計算します：
```math

[G(\sigma_k) b]_i = \left[ (\sigma_k I - A)^{-1} b \right]_{i},
```
シフト付き共役勾配法を使用して
（参照：Y. Nagai, Y. Shinohara, Y. Futamura, および T. Sakurai,[arXiv:1607.03992v2 または DOI:10.7566/JPSJ.86.014708]）。
異なる周波数 ``\sigma_k`` で ``[G(\sigma_k) b]_i`` を同時に取得できます。

入力：

* `σ` :周波数

* `A` :エルミート行列。配列、線形マップ、スパース配列を使用できます。

* `b` :入力ベクトル

* `eps` :残差（オプション）デフォルト：`1e-12`

* `maximumsteps` : 最大ステップ数（オプション）デフォルト：`20000`

出力：
* `Gij[1:M,1:size(A)[1]]`: 周波数 ``\sigma_k`` で定義された j 番目の列のグリーン関数の行列要素。
````
