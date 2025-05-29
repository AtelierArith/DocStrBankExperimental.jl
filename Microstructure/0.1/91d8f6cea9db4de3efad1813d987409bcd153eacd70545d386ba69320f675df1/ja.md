```
NetworkArg(model, protocol,params,paralinks,tissuetype,sigma,noise_type,dropoutp=0.2)
```

生物物理モデルに関連する入力を使用して、ネットワークアーキテクチャとトレーニングサンプルの数を決定し、完全に定義されたNetworkArg構造体を返します。

トレーニングサンプルの数を調整するための参考文献: Shwartz-Ziv, R., Goldblum, M., Bansal, A., Bruss, C.B., LeCun, Y., & Wilson, A.G. (2024). Just How Flexible are Neural Networks in Practice?

（簡単なタスクと小さなMLPは、効果的なモデルの複雑さが高く（ネットワークパラメータよりも多くのトレーニングサンプルをフィットできる）、より複雑なタスクと大きなMLPの場合、トレーニング効率を向上させるためにトレーニングサンプルの数をネットワークパラメータの数と同様に設定できます）
