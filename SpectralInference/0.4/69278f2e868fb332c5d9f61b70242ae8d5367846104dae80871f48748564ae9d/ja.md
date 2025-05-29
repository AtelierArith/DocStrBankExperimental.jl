```
clusters_per_cutlevel(distfun::Function, tree::Node, ncuts::Number)
```

返り値:

  * clusts: クラスタメンバーシップのベクトル。各値はそのカットでのリーフのクラスタメンバーシップを示します。リーフは各メンバーシップベクトル内でプレウォーク順に並べられています。
  * treedepths: 各 `ncuts` に対するルートからの距離
