```
InPhaseSpacePoint
```

[`PhaseSpacePoint`](@ref) に対する部分的な型特殊化であり、位相空間の入力チャネルのみが存在することを要求する関数でのディスパッチに使用できます。例えば、`_incident_flux` の実装などです。出力チャネルに対しては制限はなく、存在する場合もあれば存在しない場合もあります。

関連情報: [`OutPhaseSpacePoint`](@ref)
