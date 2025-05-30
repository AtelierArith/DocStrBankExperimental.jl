```
majortree(net::HybridNetwork; nofuse::Bool=false, unroot::Bool=false,
          keeporiginalroot::Bool=false)
```

ネットワークに表示されるメジャーツリーを抽出し、メジャーエッジを保持し、各ハイブリッドノードでマイナーエッジを削除します。

`nofuse`: trueの場合、エッジと次数2のノードはエッジ削除中に保持されます。そうでない場合、各再結合で子エッジ（ハイブリッドノードの下）を保持します：メジャーハイブリッドエッジはそれと融合します。

`unroot`: trueの場合、次数2になるとルートが削除されます。

`keeporiginalroot`: ネットワークのルートは次数1になっても保持されます。

警告:

  * `nofuse`がtrueの場合: 保持されるハイブリッドエッジ（融合なし）のγ値は変更されませんが、`ismajor`はtrueに変更されます。
  * 正しい`ismajor`属性を仮定します。
