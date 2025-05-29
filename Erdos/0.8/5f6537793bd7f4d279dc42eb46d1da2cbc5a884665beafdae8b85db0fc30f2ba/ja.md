```
count_spanning_trees(g::AGraph)
```

`g`のスパニングツリーの数を返します。これは[キルヒホッフの定理](https://en.wikipedia.org/wiki/Kirchhoff%27s_theorem)を通じて計算されます。返り値の型は浮動小数点数で、数が非常に大きくなる可能性があるためです。
