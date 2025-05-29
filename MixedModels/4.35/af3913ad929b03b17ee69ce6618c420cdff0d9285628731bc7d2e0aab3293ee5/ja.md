```
MixedModel
```

混合モデルのための抽象型です。MixedModels.jlは、`LinearMixedModel`と`GeneralizedLinearMixedModel`の2つのサブタイプを実装しています。詳細については、それぞれのドキュメントを参照してください。

この型は主に`fit`でのディスパッチに使用されます。分布とリンク関数が指定されていない場合、`LinearMixedModel`がフィットされます。分布/リンク関数が提供されると、`GeneralizedLinearModel`がフィットされますが、その分布が`Normal`でリンクが`IdentityLink`の場合、結果として得られるGLMMは`LinearMixedModel`と同等になるため、より単純で同等の`LinearMixedModel`が代わりにフィットされます。
