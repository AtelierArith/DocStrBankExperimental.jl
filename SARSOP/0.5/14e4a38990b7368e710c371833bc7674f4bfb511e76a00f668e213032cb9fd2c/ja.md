```
SARSOPEvaluator
```

XMLファイルからsarsopポリシーをシミュレートします

  * `sim_len` シミュレーションで使用するステップ数（デフォルトは10）
  * `sim_num` シミュレーションの数
  * `fast` .pomdpファイル用の高速（しかし非常に厳密な）代替パーサーを使用
  * `srand` シミュレーションのためのランダムシードを設定
  * `memory` [MB] デフォルトではメモリ制限なし。メモリ使用量が指定された値を超えると、評価者はより保守的（かつ遅い）方法に切り替えます。
  * `output_file` 結果を書き込む場所
  * `policy_filename` ポリシーファイルの場所
  * `pomdp_filename` pomdpxファイルの場所
