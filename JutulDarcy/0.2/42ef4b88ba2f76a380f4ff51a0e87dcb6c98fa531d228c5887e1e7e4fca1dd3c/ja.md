```
component_mass_fluxes!(q, face, state, model, flux_type, kgrad, upw)
```

与えられた面に対する特定のシステムの成分フラックスの実装。成分ごとに1つのエントリを持つ`StaticVector`を返す必要があります。
