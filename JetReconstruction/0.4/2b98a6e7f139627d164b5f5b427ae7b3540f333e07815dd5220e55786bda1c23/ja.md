```
exclusive_jets(clusterseq::ClusterSequence{U}; dcut = nothing, njets = nothing, T = LorentzVectorCyl) where {U}
```

クラスタリングシーケンスのすべての排他的ジェットを返します。特定の数のジェットまたは最大距離パラメータに対するカットのいずれかを指定できます。

# 引数

  * `clusterseq::ClusterSequence`: クラスタリング履歴とジェットを含む `ClusterSequence` オブジェクト。
  * `dcut::Union{Nothing, Real}`: 排他的ジェットを定義するために使用される距離パラメータ。`dcut` が提供されると、排他的ジェットの数はこのパラメータに基づいて計算されます。
  * `njets::Union{Nothing, Integer}`: 計算される排他的ジェットの数。`njets` が提供されると、距離パラメータ `dcut` はこの数に基づいて計算されます。
  * `T = LorentzVectorCyl`: 選択されたジェットに使用される戻り値の型。

**注意**: `dcut` または `njets` のいずれかを提供する必要があります（ただし両方は不可）。

# 戻り値

  * 排他的ジェットを表す `T` オブジェクトの配列。

有効な戻り値の型は `LorentzVectorCyl` と入力 `clusterseq` のジェット型 (`U` - 使用されたアルゴリズムに応じて `PseudoJet` または `EEjet`) です（注: 将来的には `FourMomentumBase` の任意のサブタイプに進化します; 現在認識されない型は `LorentzVectorCyl` を返します）。

# 例外

  * `ArgumentError`: `dcut` も `njets` も提供されていない場合。
  * `ArgumentError`: `ClusterSequence` オブジェクトで使用されるアルゴリズムが排他的ジェットに適していない場合。
  * `ErrorException`: クラスタシーケンスが不完全で排他的ジェットが利用できない場合。

# 例

```julia
exclusive_jets(clusterseq, dcut = 20.0)
exclusive_jets(clusterseq, njets = 3, T = PseudoJet)
```
