```
jet_filtering(jet, clusterseq, filter) -> PseudoJet
```

指定された半径と数に基づいて、最もハードなサブジェットのみを保持するようにジェットをフィルタリングします。

# 引数:

  * `jet::PseudoJet`: フィルタリングするジェットを表すPseudoJetインスタンス。
  * `clusterseq::ClusterSequence`: ジェットの履歴を含むClusterSequence。
  * `filter::JetFilter`: 半径とサブジェットの数を指定するフィルタインスタンス。

# 戻り値:

  * `PseudoJet`: 最もハードなサブジェットで構成されたフィルタリングされたジェット。
