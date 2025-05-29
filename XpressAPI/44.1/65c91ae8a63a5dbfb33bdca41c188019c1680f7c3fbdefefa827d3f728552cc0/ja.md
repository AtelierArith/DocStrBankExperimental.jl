```
XPRSaddcbchgbranchobject(prob, cb, priority)
```

# 引数

  * `cbprob`: コールバック関数 `chgbranchobject` に渡される問題。
  * `branch`: オプティマイザによって選択された候補ブランチデータ。候補が存在しない場合は `nothing` になります。
  * `newbranch`: オプティマイザの選択を置き換えるためのオプションの新しいブランチデータ。`branch` または `nothing` が返された場合、変更は適用されません。

`cb` はこのシグネチャで呼び出されます：

```
cb(cbprob, branch)::newbranch
```
