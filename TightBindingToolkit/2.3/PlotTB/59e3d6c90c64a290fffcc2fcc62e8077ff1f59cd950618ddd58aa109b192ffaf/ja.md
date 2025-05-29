```julia
Plot_UnitCell!(uc::UnitCell ; range::Int64 = 1, bond_cmp::Symbol = :matter, sub_cmp::Symbol = :rainbow, plot_conjugate::Bool=false, plot_labels::Vector{String} = unique(getproperty.(uc.bonds, :label)), plot_arrows::Bool = true, bond_opacity::Float64 = 0.6, site_size::Float64 = 16.0, bond_thickness::Tuple{Float64, Float64} = (4.0, 2.0), bond_rev::Bool=false, plot_lattice::Bool=false)
```

`UnitCell`をプロットするための関数。

  * `range`は、実空間でプロットされるUnitCellの範囲を決定します。デフォルトは±1です。
  * `bond_cmp`は、異なるホッピングタイプを区別するために選択されたカラースキームを決定します。
  * `plot_conjugate`は、`UnitCell`内の結合の共役もプロットするかどうかを切り替えます。
  * `sub_cmp`は、異なるサブ格子のために選ばれたカラースキームです。
  * `plot_labels`は、プロットされる結合ラベルのベクトルです。
  * `plot_arrows` : 結合に矢印をプロットするかどうか。
  * `bond_opacity` : プロットされる結合のアルファ値。
  * `bond_thickness` : プロットされる結合の線幅。
  * `site_size`: サブ格子点のサイズ。
  * `plot_lattice`: すべてのサイトに結合をプロットするか、1つのユニットセルのみにプロットするか。
