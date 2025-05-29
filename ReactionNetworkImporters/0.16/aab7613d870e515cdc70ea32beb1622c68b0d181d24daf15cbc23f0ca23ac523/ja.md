```
loadrxnetwork(mn::MatrixNetwork; name = gensym(:ReactionSystem))
```

`MatrixNetwork`を`ParsedReactionNetwork`に変換するために、`ReactionSystem`を構築します。

# 引数

  * `mn::MatrixNetwork`: ストイキオメトリック行列、反応速度式、種、パラメータを含む`MatrixNetwork`オブジェクト。
  * `name::Symbol`: (オプション) 結果の`ReactionSystem`の名前。デフォルトでは生成されたシンボルが使用されます。

# 戻り値

`ParsedReactionNetwork` 

# 注意事項

  * `MatrixNetwork`は、基質（`substoich`）と生成物（`prodstoich`）のストイキオメトリック行列が同じサイズである必要があります。
  * ストイキオメトリック行列は`numspecies x numrxs`であると仮定され、各エントリ`(i, j)`は反応`j`における種`i`のストイキオメトリック係数を表します。
  * `MatrixNetwork`の`species`フィールドが空の場合、種のシンボルは自動的に生成されます。
  * `t`フィールドは独立変数（例：時間）を指定します。提供されない場合、デフォルトの時間変数が使用されます。

# 例

```julia
using Catalyst

# MatrixNetworkを定義
rateexprs = [1.0, 2.0]
substoich = [1 0; 0 1]
prodstoich = [0 1; 1 0]
species = [@species A(t), B(t)]
params = [@parameters k1, k2]
mn = MatrixNetwork(rateexprs, substoich, prodstoich; species = species, params = params)

# ParsedReactionNetworkに変換
parsed_network = loadrxnetwork(mn, name = :MyReactionSystem)
```
