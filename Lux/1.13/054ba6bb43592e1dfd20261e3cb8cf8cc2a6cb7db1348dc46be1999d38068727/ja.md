```
FluxLayer(layer)
```

FluxとLuxの間の互換性レイヤーとして機能します。これは内部で`Optimisers.destructure` APIを使用します。

!!! warning
    Luxは`destructure` + `Flux`の制限を克服するために書かれました。このレイヤーを使用するのではなく、Luxでレイヤーを書き直すことをお勧めします。


!!! warning
    モデルにこのレイヤーを導入すると、`Optimisers.destructure`の動作のために型の不安定性が生じます。


## 引数

  * `layer`: Fluxレイヤー

## パラメータ

  * `p`: `layer`のフラット化されたパラメータ
