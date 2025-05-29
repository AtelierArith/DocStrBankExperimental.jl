```
boundary_condition_slip_wall(u_inner, normal_direction, x, t, surface_flux_function,
                             equations::CompressibleEulerEquations2D)
```

スリップ壁条件の境界数値表面フラックスを決定します。壁での法線速度をゼロに設定します。密度は内部解状態から取得され、圧力は1Dリーマン問題の正確な解として計算されます。この境界状態に関する詳細は、以下の論文にあります：

  * J. J. W. van der Vegt と H. van der Ven (2002) スリップフロー境界条件の不連続ガレルキン離散化におけるオイラー方程式のガス動力学 [PDF](https://reports.nlr.nl/bitstream/handle/10921/692/TP-2002-300.pdf?sequence=1)

1D圧力リーマン解に関する詳細は、以下の書籍のセクション6.3.3にあります：

  * Eleuterio F. Toro (2009) リーマンソルバーと流体力学の数値手法：実践的な入門 第3版 [DOI: 10.1007/b79761](https://doi.org/10.1007/b79761)

[`UnstructuredMesh2D`](@ref)、[`P4estMesh`](@ref)、または[`T8codeMesh`](@ref)と一緒に使用する必要があります。
