```
ContractingRENParams(nv, A, B, C, D; ...)
```

`ContractingRENParams`の代替コンストラクタで、状態空間モデルを持つ**安定した**離散時間線形システムからRENを初期化します。

$$
\begin{align*}
x_{t+1} &= Ax_t + Bu_t \\
y_t &= Cx_t + Du_t.
\end{align*}
$$

[TODO:] このメソッドはしばらく使用されていないか、テストされていません。もし役に立つと思われる場合は、お知らせください。完全なサポートとテストを追加します！ :) [TODO:] αbar ≠ 1.0に対応させる。
