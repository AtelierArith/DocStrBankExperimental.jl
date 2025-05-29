```
mass_drop(jet, clusterseq, tag) -> PseudoJet
```

質量ドロップタグ付け条件を満たすジェット内のサブジェットを特定します。このメソッドは、質量と距離の閾値を満たす最初のジェットで停止します。

# 引数:

  * `jet::PseudoJet`: タグ付けするジェットを表すPseudoJetインスタンス。
  * `clusterseq::ClusterSequence`: ジェットクラスタリング履歴を持つClusterSequence。
  * `tag::MassDropTagger`: 質量ドロップパラメータを提供するMassDropTaggerインスタンス。

# 戻り値:

  * `PseudoJet`: タグ付けが成功した場合、質量ドロップ条件を満たすジェット（またはサブジェット）、そうでない場合はゼロ運動量のPseudoJet。
