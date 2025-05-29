```
boundary_var_domain_names(::AbstractBC, ::ClimaLand.AbstractBoundary)
```

モデルの補助状態に追加するための追加変数のドメイン名のリスト。これは、PDEを解くモデルに対して、デフォルトで上部または下部境界フラックスフィールドの表面ドメインにストレージを追加するが、使用される境界条件のタイプに応じて拡張可能です。

`auxiliary_var_domain_names`を使用するのと同じ方法で、`boundary_vars`と一緒に使用します。
