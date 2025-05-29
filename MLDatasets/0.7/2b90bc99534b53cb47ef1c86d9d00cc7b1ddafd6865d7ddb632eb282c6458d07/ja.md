```
Cora()
```

Cora引用ネットワークデータセットはRef. [1]からのものです。ノードは文書を表し、エッジは引用リンクを表します。各ノードには1433次元の事前定義された特徴があります。このデータセットはノード分類タスクのために設計されています。このタスクは特定の論文のカテゴリを予測することです。このデータセットはRef. [2]から取得されました。

# 統計

  * ノード: 2708
  * エッジ: 10556
  * クラス数: 7
  * ラベル分割:

      * トレイン:  140
      * バリデーション:    500
      * テスト:  1000

この分割は元の論文[1]で使用されたものであり、すべてのノードを考慮していません。

# 参考文献

[1]: [Deep Gaussian Embedding of Graphs: Unsupervised Inductive Learning via Ranking](https://arxiv.org/abs/1707.03815)

[2]: [Planetoid](https://github.com/kimiyoung/planetoid)
