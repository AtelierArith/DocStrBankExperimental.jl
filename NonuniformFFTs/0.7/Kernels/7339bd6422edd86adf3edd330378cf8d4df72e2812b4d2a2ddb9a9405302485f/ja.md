```
BSplineKernel <: AbstractKernel
BSplineKernel()
```

Bスプラインスプレッディングカーネルを表します。

Bスプラインの次数 $n$ は、カーネルの半幅 $M$ に直接関連しており、$n = 2M$ です（多項式の次数は $n - 1$ です）。

# 定義

次数 $n$ のBスプラインは、そのフーリエ変換を通じて定義できます：

$$
ϕ̂(k) = Δx \operatorname{sinc}^n \left( \frac{k Δx}{2} \right)
$$

ここで、$Δx$ はオーバーサンプリンググリッドの間隔であり、$\operatorname{sinc}$ は[正規化されていないsinc関数](https://en.wikipedia.org/wiki/Sinc_function)です。

# 実装の詳細

実装では、このカーネルは[デ・ブールのアルゴリズム](https://en.wikipedia.org/wiki/De_Boor%27s_algorithm)を使用して評価されます。
