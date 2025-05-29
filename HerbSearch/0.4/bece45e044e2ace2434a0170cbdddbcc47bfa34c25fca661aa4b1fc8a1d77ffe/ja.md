```
@enum SynthResult optimal_program=1 suboptimal_program=2
```

合成手続きの可能な結果の表現。 現在、2つの可能な結果があります：

  * `optimal_program`: 合成されたプログラムは、プログラム仕様全体を満たしています。
  * `suboptimal_program`: 合成されたプログラムは、プログラム仕様全体を満たしていませんが、評価者から最高のスコアを得ました。
