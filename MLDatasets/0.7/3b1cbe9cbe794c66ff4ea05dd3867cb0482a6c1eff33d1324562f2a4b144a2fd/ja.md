```
KarateClub()
```

ザカリーの空手クラブデータセットは、元々Ref [1]に登場しました。

ネットワークには34のノード（空手クラブのメンバー）が含まれています。ノードは78の無向および無重みのエッジで接続されています。エッジは、2人のメンバーがクラブの外で相互作用したかどうかを示しています。

ノードのラベルは、メンバーがどのコミュニティまたは空手クラブに属しているかを示しています。クラブに基づくラベルは、Ref [1]の元のデータセットに従っています。コミュニティラベルは、Ref [2]に従ったモジュラリティベースのクラスタリングによって取得されます。データはRef [3]および[4]から取得されます。ユニークなラベルごとに1つのノードがトレーニングデータとして使用されます。

# 参考文献

[1]: [小グループにおける対立と分裂のための情報フローモデル](http://www1.ind.ku.dk/complexLearning/zachary1977.pdf)

[2]: [グラフ畳み込みネットワークによる半教師あり分類](https://arxiv.org/abs/1609.02907)

[3]: [PyTorch Geometric 空手クラブデータセット](https://pytorch-geometric.readthedocs.io/en/latest/_modules/torch_geometric/datasets/karate.html#KarateClub)

[4]: [NetworkX ザカリーの空手クラブデータセット](https://networkx.org/documentation/stable/_modules/networkx/generators/social.html#karate_club_graph)
