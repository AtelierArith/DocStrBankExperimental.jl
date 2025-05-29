```
jet_trimming(jet, clusterseq, trim) -> PseudoJet
```

指定された割合未満の横運動量を持つサブジェットを削除することによって、ジェットをトリミングします。

# 引数:

  * `jet::PseudoJet`: トリミングするジェットを表すPseudoJetインスタンス。
  * `clusterseq::ClusterSequence`: ジェットの履歴を含むClusterSequence。
  * `trim::JetTrim`: トリミングパラメータを指定するTrimインスタンス。

# 戻り値:

  * `PseudoJet`: 残されたサブジェットで構成されたトリミングされたジェット。
