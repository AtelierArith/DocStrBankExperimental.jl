```
boundary_condition_slip_wall(u_inner, orientation, direction, x, t,
                             surface_flux_function, equations::CompressibleEulerEquations1D)
```

スリップ壁条件の境界数値表面フラックスを決定します。壁での法線速度をゼロに設定します。密度は内部解状態から取得され、圧力は1Dリーマン問題の正確な解として計算されます。この境界状態に関する詳細は、以下の論文にあります：

  * J. J. W. van der Vegt と H. van der Ven (2002) スリップフロー境界条件の不連続ガレルキン離散化におけるガス動力学のオイラー方程式 [PDF](https://reports.nlr.nl/bitstream/handle/10921/692/TP-2002-300.pdf?sequence=1)

    [`TreeMesh`](@ref) と一緒に使用する必要があります。
