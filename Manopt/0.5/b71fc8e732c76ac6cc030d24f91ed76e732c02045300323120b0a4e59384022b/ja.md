```
SymmetricLinearSystemObjective{E<:AbstractEvaluationType,TA,T} <: AbstractManifoldObjective{E}
```

目的をモデル化します

$$
f(X) = \frac{1}{2} \lVert \mathcal A[X] + b \rVert_{p}^2,\qquad X ∈ T_{p}\mathcal M,
$$

これは、マンifold $\mathcal M$ の点 $p$ における接空間 $T_{p}\mathcal M$ で定義されています。

言い換えれば、これは線形対称演算子とベクトル関数のために $\mathcal A = -b(p)$ を解く目的です。右辺のマイナスに注意してください。これは、この目的が特にニュートン様方程式を（反復的に）解くために特化されていることを示しています。

# フィールド

  * `A!!`: 接空間上の対称線形演算子
  * `b!!`: 勾配関数

ここで、`A!!` は割り当て演算子 `(M, p, X) -> Y` またはインプレース演算子 `(M, Y, p, X) -> Y` として機能し、同様に `b!!` は関数 `(M, p) -> X` または `(M, X, p) -> X` として機能します。最初のバリアントは結果のために割り当てを行い、2番目のバリアントはインプレースで動作します。

# コンストラクタ

```
SymmetricLinearSystemObjective(A, b; evaluation=AllocatingEvaluation())
```

2つの部分が割り当てを行うかインプレースで動作するかを指定して目的を生成します。
