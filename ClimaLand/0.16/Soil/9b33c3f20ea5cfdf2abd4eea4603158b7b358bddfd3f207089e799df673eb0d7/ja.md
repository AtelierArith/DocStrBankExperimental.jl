```
boundary_var_types(::Soil.EnergyHydrology{FT}, ::AbstractEnergyHydrologyBC, ::ClimaLand.AbstractBoundary) where {FT}
```

エネルギー水文学モデルの補助状態に追加された追加変数のドメイン名のリストで、デフォルトでは境界フラックスフィールドのストレージを追加します。

水と熱の境界条件を供給するため、これらを `top_bc` と `bottom_bc` という名前の NamedTuple に保存することが便利であることがわかりました。
