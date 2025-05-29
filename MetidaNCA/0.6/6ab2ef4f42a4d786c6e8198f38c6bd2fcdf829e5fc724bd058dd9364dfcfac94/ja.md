```
pkplot(subj; ls = false, elim = false, xticksn = :auto, yticksn = :auto, kwargs...)
```

被験者のプロット

  * `ls` - 対数スケールでの濃度;
  * `elim` - 排除曲線を描画;
  * `xticksn` - x軸の目盛りの数;
  * `yticksn` - y軸の目盛りの数;

*その他のキーワード:*

  * `plotstyle` - PKPLOTSTYLEからの事前定義されたプロットスタイル;
  * `drawbl` (`false`) - ベースラインを描画、PDSubjectのみに適用;
  * `drawth` (`false`) - 閾値を描画、PDSubjectのみに適用;
  * `drawdt` (`false`) - 投与時間を描画;
