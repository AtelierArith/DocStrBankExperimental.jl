`struct PooledSparseProduct` :  これは、融合された（テンソル）積とプーリング操作を実装します。$N$ 個の埋め込み $\phi^{(i)}_{k_i}$ が与えられたとすると、プールされたスパース積は次の形式の特徴ベクトルを生成します。

$$
A_{k_1, \dots, k_N} = \sum_{j} \prod_{t = 1}^N \phi^{(t)}_{k_t}(x_j)
$$

ここで、$x_j$ は入力のリスト（多集合）です。

標準的な例は次のとおりです。

$$
A_{nlm} = \sum_{j} R_{nl}(r_j, \mu_j) Y_l^m( \hat{\bm r}_j ),
$$

ここで、$R_{nl}$ は放射状の埋め込みであり、カテゴリ変数 $\mu_j$ に依存する可能性があり、$Y_l^m$ は球面調和関数です。

### コンストラクタ

```julia
PooledSparseProduct(spec)
```

ここで `spec` は $(k_1, \dots, k_N)$ のタプルまたはベクトルのリスト、または各列がそのようなタプルを指定する `AbstractMatrix` です。
