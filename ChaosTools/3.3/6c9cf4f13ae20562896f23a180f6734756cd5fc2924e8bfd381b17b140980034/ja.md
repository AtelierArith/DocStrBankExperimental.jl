```
dyca(data, eig_threshold) -> eigenvalues, proj_mat, projected_data
```

与えられた `data` [^Uhl2018] の動的成分分析（DyCA）を計算して、次元削減を行います。

固有値、射影行列、および次元削減されたデータ（これは単に `data*proj_mat` です）を返します。

## キーワード引数

  * norm_eigenvectors=false : true の場合、固有ベクトルを正規化します

## 説明

動的成分分析（DyCA）は、多変量の高次元決定論的データセットの次元を削減するための射影ベクトルを検出する方法です。PCA や ICA のような確率性の仮定を行う方法とは異なり、DyCA は時系列に対する決定性の仮定に依存し、一般化された固有値問題の解に基づいています。適切な固有値の閾値を選択し、固有値問題を解決した後、得られた固有ベクトルを使用して高次元データセットを低次元に射影します。得られた固有値は、調査されたデータに対する線形決定論の仮定の質を測定します。さらに、値が約 1.0 の一般化された固有値の数は、データセットに含まれる線形方程式の数の尺度となります。この特性は、時系列の中で非常に決定論的な部分を持つ領域を検出するのに役立ち、また高次元時空間データのリザーバコンピューティングの前処理ステップとしても有用です。

私たちが解決する一般化された固有値問題は次のとおりです：

$$
C_1 C_0^{-1} C_1^{\top} \bar{u} = \lambda C_2 \bar{u}

$$

ここで、$C_0$ はデータ自身との相関行列、$C_1$ はデータとその導関数との相関行列、$C_2$ はデータの導関数自身との相関行列です。固有値が約 1 の固有ベクトル $\bar{u}$ とその $C_1^{-1} C_2 u$ 対応物は、データが射影される空間を形成します。

[^Uhl2018]: B Seifert, K Korn, S Hartmann, C Uhl, *Dynamical Component Analysis (DYCA): Dimensionality Reduction for High-Dimensional Deterministic Time-Series*, 10.1109/mlsp.2018.8517024, 2018 IEEE 28th International Workshop on Machine Learning for Signal Processing (MLSP)

```
