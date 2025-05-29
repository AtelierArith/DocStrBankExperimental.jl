```
add_subgraph(graph::OptiGraph; name::Symbol=Symbol(:sg,gensym()))
```

既存のサブグラフをオプティグラフに追加します。サブグラフは他のオプティグラフの一部であってはなりません。また、オプティグラフに既に存在するノードを持っていてはいけません。
