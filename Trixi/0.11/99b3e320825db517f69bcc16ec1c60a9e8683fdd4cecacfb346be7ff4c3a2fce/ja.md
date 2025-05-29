```
ViscousFormulationLocalDG(penalty_parameter)
```

「時間依存対流拡散系のための局所不連続ガレルキン法」(Cockburn and Shu, 1998) における局所DG (LDG) フラックス。

放物線的な「アップウィンドウ」ベクトルは現在 `TreeMesh` に対して実装されています。他のすべてのメッシュタイプに対して、LDG ソルバーは LDG タイプのペナルティを持つ [`ViscousFormulationBassiRebay1`](@ref) と同等です。

  * Cockburn and Shu (1998). 時間依存対流拡散系のための局所不連続ガレルキン法 [DOI: 10.1137/S0036142997316712](https://doi.org/10.1137/S0036142997316712)
