```
SARSOPSolver
```

SARSOPのベースソルバータイプ。以下のエントリを持つオプション辞書を含みます：

  * 'fast': .pomdpファイル用の高速（しかし非常に選択的な）代替パーサーを使用
  * 'randomization': サンプリングアルゴリズムのためにランダム化をオンにする
  * 'precision': 目標精度に達したときに実行を終了
  * 'timeout':  [秒] 実行時間が指定された値を超えると、pomdpsolはポリシーを書き出し、終了します
  * 'memory': [MB] メモリ使用量が指定された値を超えると、pomdpsolはポリシーを書き出し、終了します
  * 'trial-improvement-factor': 境界間のギャップがこの値に達したときに終了
  * 'policy-interval':  ポリシーファイルの2回の連続書き出しの間の時間間隔
  * `verbose`: [true/false] ソルバーからの出力を印刷するかどうか。デフォルト: true
