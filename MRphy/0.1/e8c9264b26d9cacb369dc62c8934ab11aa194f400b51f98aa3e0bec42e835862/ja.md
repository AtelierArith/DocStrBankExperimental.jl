```
spincube = mSpinCube(dim::Dims{3}, fov; ofst, Δf, T1, T2, γ)
spincube = mSpinCube(mask::BitArray{3}, fov; ofst, Δf, T1, T2, γ)
```

`dim`、`mask`、`T1`、`T2`、および`γ`は`mSpinArray`コンストラクタに渡されます。

定期的に配置されたスピンのセットをモデル化するために設計された`AbstractSpinCube`をインスタンス化する例示的な構造体。

# フィールド:

*不変*:

  * `spinarray::AbstractSpinArray` (1,): 継承された`AbstractSpinArray`構造体
  * `fov ::TypeND(L0D, [2])` (1, 3): 視野。
  * `ofst::TypeND(L0D, [2])` (1, 3): 磁場アイソセンターからのfovオフセット。
  * `loc ::TypeND(L0D, [2])` (nM, 3): スピンの位置。

*可変*:

  * `Δf::TypeND(F0D, [0,1])` (1,) または (nM,): オフ共鳴マップ。

参照: [`AbstractSpinCube`](@ref)。
