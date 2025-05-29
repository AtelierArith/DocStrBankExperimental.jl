```
optimize_code(eincode, size_dict, optimizer = GreedyMethod(), simplifier=nothing, permute=true) -> optimized_eincode
```

einsum収束コードを最適化し、テンソルネットワーク収束の時間/空間複雑度を削減します。`NestedEinsum`インスタンスを返します。入力引数は次のとおりです。

  * `eincode`はeinsum収束コードインスタンスで、`DynamicEinCode`、`StaticEinCode`、または`NestedEinsum`のいずれかです。
  * `size`は「エッジラベル=>エッジサイズ」の辞書で、サイズ情報を含んでいます。`uniformsize(eincode, 2)`を使用して均一なサイズを作成できます。
  * `optimizer`は`CodeOptimizer`インスタンスで、`GreedyMethod`、`Treewidth`、`KaHyParBipartite`、`SABipartite`、または`TreeSA`のいずれかである必要があります。詳細については、それらのドキュメント文字列を確認してください。
  * `simplifier`は`MergeVectors`または`MergeGreedy`のいずれかです。
  * `permute`がtrueの場合、順序を最適化します。

### 例

```jldoctest
julia> using OMEinsum

julia> code = ein"ij, jk, kl, il->"
ij, jk, kl, il -> 

julia> optimize_code(code, uniformsize(code, 2), TreeSA());
```
