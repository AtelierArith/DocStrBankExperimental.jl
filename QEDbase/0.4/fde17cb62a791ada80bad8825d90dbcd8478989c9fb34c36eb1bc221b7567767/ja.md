```
AbstractInPhaseSpacePoint
```

[`AbstractPhaseSpacePoint`](@ref) に対する部分的な型特殊化であり、フェーズスペースの入力チャネルのみが存在することを要求する関数でのディスパッチに使用できます。例えば、[`_incident_flux`](@ref) の実装などです。出力チャネルに対しては制限はなく、存在する場合もあれば存在しない場合もあります。

参照: [`AbstractOutPhaseSpacePoint`](@ref)
