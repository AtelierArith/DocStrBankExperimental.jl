```
LayerNormRule()
```

LRP-LN ルール。`LayerNorm` レイヤーで使用されます。

# 定義

レイヤー出力での関連性 $R^{k+1}$ をレイヤー入力での $R^k$ に伝播します。

$$
R_i^k = \sum_j\frac{a_i^k\left(\delta_{ij} - 1/N\right)}{\sum_l a_l^k\left(\delta_{lj}-1/N\right)} R_j^{k+1}
$$

アフィン変換を通じた関連性は、デフォルトで [`ZeroRule`](@ref) を使用して伝播されます。

`LayerNorm` レイヤー内のアフィン変換に特別なルールを割り当てたい場合は、モデルに対して `canonize` を呼び出してください。これにより、`LayerNorm` レイヤーが次のように分割されます。

1. アフィン変換のない `LayerNorm` レイヤー
2. アフィン変換を実装する `Scale` レイヤー

これらの2つのレイヤーに別々のルールを割り当てることができます。

# 参考文献

  * A. Ali et al., *XAI for Transformers: Better Explanations through Conservative Propagation*
