与えられた時系列のスペクトルエンベロープを計算します。

```
input:

- ts: 分析する時系列
- m : 希望する平滑化の度合い。
      mは、平滑化を実現するために与えられた点と混合される隣接点の数に対応します。

output:

- Frequencies : 関与する周波数に対応する点のリスト。
                [0,0.5]に含まれます。
- amplitude : 各与えられた周波数点に対するスペクトルエンベロープの値。
- eigenvectors : 各周波数点に対する異なるカテゴリの最適スケーリング。
- categories : データに存在するカテゴリのリスト。
```
