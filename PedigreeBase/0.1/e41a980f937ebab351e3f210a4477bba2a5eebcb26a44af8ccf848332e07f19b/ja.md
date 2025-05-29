```
perm,invp,subpedlist = subset_ped(pedlist,idlist)
```

`pedlist`の部分集合を作成し、2つの置換ベクトルを生成します: `perm[newid]=oldid` と `invp[oldid]=newid`。部分集合には`idlist`にリストされた動物とその祖先が含まれます。部分集合の系譜は時系列でソートされています。

この関数は`find_ped_order`と`extract_ped`のラッパーです。詳細については関数を参照してください。
