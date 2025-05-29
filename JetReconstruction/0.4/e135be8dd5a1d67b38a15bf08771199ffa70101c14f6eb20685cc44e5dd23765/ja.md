```
inclusive_jets(clusterseq::ClusterSequence{U}; ptmin = 0.0, T = LorentzVectorCyl) where {U}
```

指定された `ClusterSequence` のすべてのインクルーシブジェットを pt > ptmin で返します。

# 引数

  * `clusterseq::ClusterSequence`: クラスタリング履歴とジェットを含む `ClusterSequence` オブジェクト。
  * `ptmin::Float64 = 0.0`: インクルーシブジェットのための最小横運動量 (pt) 閾値。
  * `T = LorentzVectorCyl`: 選択されたジェットに使用される戻り値の型。

# 戻り値

インクルーシブジェットを表す `T` オブジェクトの配列。

# 説明

この関数は、指定された `ClusterSequence` オブジェクトからインクルーシブジェットを計算します。クラスタリング履歴を反復処理し、各親ジェットの横運動量をチェックします。横運動量が `ptmin` 以上であれば、そのジェットはインクルーシブジェットの配列に追加されます。

有効な戻り値の型は `LorentzVectorCyl` と、入力 `clusterseq` のジェット型 (`U` - 使用されたアルゴリズムに応じて `PseudoJet` または `EEjet`) です (注: 将来的には `FourMomentumBase` の任意のサブタイプに進化します; 現在認識されていない型は `LorentzVectorCyl` を返します)。

# 例

```julia
inclusive_jets(clusterseq; ptmin = 10.0)
```
