```
CanInstallRulesTrait
```

このトレイトを持つことで、知識ベースのルートノードはネットワークにルールを追加するための `install` メソッドを持つことができます。

このトレイトを `YourType` に追加するには、次のようにします。

```
CanInstallRulesTrait(::Type{<:YourType}) = CanInstallRulesTrait())
```
