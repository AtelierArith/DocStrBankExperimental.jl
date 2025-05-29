```
knuthbendix(rws::AbstractRewritingSystem)
knuthbendix(settings::Settings, rws::AbstractRewritingSystem)
```

再帰系 `rws` に対して、`method` で定義されたアルゴリズムを使用してクヌース＝ベンディックス完了を実行します。

!!! warn
    完了アルゴリズムによって返される再帰系は、必ずしも結合的ではない場合があります。通常、これは以下の理由によって発生します。

      * `rws` に保存されているルールの数が `settings` で許可されている数を超える場合、
      * 完了プロセスが手動で中断された場合、
      * または `settings` がアルゴリズムに特定の重要なペアの処理をスキップすることを許可している場合。

    再帰系が **結合的でない** ことを常に仮定すべきです。 [`isconfluent`](@ref) が `true` を返さない限り。


手動で中断されない限り、返される再帰系は簡約されます。
