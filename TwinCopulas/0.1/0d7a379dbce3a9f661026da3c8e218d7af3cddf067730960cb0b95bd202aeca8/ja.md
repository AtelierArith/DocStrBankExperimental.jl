```
AsymLogCopula{P}
```

フィールド:

  * α::Real - 依存パラメータ
  * θ::Vector - 非対称パラメータ (サイズ 2)

コンストラクタ

```
AsymLogCopula(α, θ)
```

非対称二変量ロジスティックコピュラは、1つの依存パラメータ $\alpha \in [1, \infty]$ と2つの非対称パラメータ $\theta_{i} \in [0,1], i=1,2$ によってパラメータ化されます。これは、ピカンズ依存関数を持つ極値コピュラです:

$$
A(t) = (\theta_1^{\alpha}(1-t)^{\alpha} + \theta_2^{\alpha}t^{\alpha})^{\frac{1}{\alpha}} + (\theta_1 - \theta_2)t + 1 - \theta_1
$$

参考文献:

  * [Tawn1988](@cite) 二変量極値理論: モデルと推定. Biometrika, 1988.
