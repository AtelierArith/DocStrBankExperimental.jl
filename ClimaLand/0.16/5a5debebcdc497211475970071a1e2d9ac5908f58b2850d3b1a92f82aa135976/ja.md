```
boundary_var_types(model::AbstractModel{FT}, ::AbstractBC, ::ClimaLand.AbstractBoundary) where {FT}
```

境界条件を使用するタイプに応じて拡張できるが、デフォルトでは、上部または下部境界フラックスフィールドのために表面領域にスカラー変数を追加するモデルの補助状態に追加する変数のタイプのリスト。

`boundary_vars`と一緒に使用し、`auxiliary_var_types`を使用するのと同じ方法で使用します。スカラーの使用は、単一のPDEを持つモデルに適しています。複数のPDEを持つモデルは、複数のスカラー場を供給する必要があります。
