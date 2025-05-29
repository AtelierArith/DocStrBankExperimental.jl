```julia
productbelief(
    denspts,
    manifold,
    dens,
    N;
    asPartial,
    dbg,
    logger
)

```

`dens`の積（オプションの部分的信念を含む）を掛け合わせるための提案として取ります。

## 注意事項

  * 提案の部分次元がのみであっても、全次元のポイントを返します。

      * '他の'次元は、受信した`denspts`から変更されません
  * `d`次元の積近似
  * 個々のバッチで変数を処理するためにApproxManifoldProductsを組み込みます。

DevNotes

  * TODO [`AMP.manifoldProduct`](@ref)と統合する、特に部分的なものに関して。
