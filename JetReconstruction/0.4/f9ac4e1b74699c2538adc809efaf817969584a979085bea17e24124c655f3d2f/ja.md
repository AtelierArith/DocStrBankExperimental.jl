```
soft_drop(jet, clusterseq, tag) -> PseudoJet
```

ソフトドロップグルーミングを適用して、ジェットからソフトで広角の放射を除去します。この関数はジェットを再クラスタリングし、サブジェットに対してソフトドロップ条件を反復的にチェックします。

# 引数:

  * `jet::PseudoJet`: グルーミングするPseudoJetインスタンス。
  * `clusterseq::ClusterSequence`: ジェットの履歴を含むClusterSequence。
  * `tag::SoftDropTagger`: ソフトドロップパラメータを持つSoftDropTaggerインスタンス。

# 戻り値:

  * `PseudoJet`: グルーミングされたジェット、またはグルーミングに失敗した場合はゼロモーメンタムのPseudoJet。
