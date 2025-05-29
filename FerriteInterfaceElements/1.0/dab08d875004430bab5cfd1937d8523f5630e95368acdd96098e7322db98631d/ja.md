```
insert_interfaces(grid, domain_names; topology=ExclusiveTopology(grid))
```

`domain_names`で定義されたドメインの間に`InterfaceCell`を挿入した新しいグリッドを返します。新しいグリッドは追加のセルセットを提供します。セット`"interfaces"`にはすべての新しい`InterfaceCell`が含まれ、ドメイン名の組み合わせごとに2つのセットが提供されます：`"domain1-domain2-inertface"`と`"domain2-domain1-inertface"`はどちらも同じ`Set`を使用します。
