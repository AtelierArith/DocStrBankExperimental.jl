```
merge_cliques!(cg::CliqueGraph; verbose=false)
```

`cg`内のクリークを貪欲にマージします。最初は、最も大きな`weight_function`を持つペアから始めます。すべてのクリークのペアが非正の重みになると停止します。

# 参考文献

  * [A clique graph based merging strategy for decomposable SDPs](https://arxiv.org/pdf/1911.05615) by Michael Garstka, Mark Cannon, Paul Goulart
