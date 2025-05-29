prognostic*domain*names(m::AbstractModel)

予測変数のドメイン名をタプルの形式で返します。

例: (:surface, :surface, :subsurface)。

このデフォルトは、モデルに予測変数がないことを示唆しており、これは無効なモデル設定です。この関数はすべてのモデルに対して拡張されることを意図しています。
