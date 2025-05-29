```
AutoFiniteDiff{T1,T2,T3}
```

自動微分のために[FiniteDiff.jl](https://github.com/JuliaDiff/FiniteDiff.jl)バックエンドを選択するために使用される構造体。

[ADTypes.jl](https://github.com/SciML/ADTypes.jl)によって定義されています。

# コンストラクタ

```
AutoFiniteDiff(; fdtype=Val(:forward), fdjtype=fdtype, fdhtype=Val(:hcentral), relstep=nothing, absstep=nothing)
```

# フィールド

  * `fdtype::T1`: 有限差分タイプ
  * `fdjtype::T2`: ヤコビアンのための有限差分タイプ
  * `fdhtype::T3`: ヘッセ行列のための有限差分タイプ
  * `relstep`: 相対有限差分ステップサイズ
  * `absstep`: 絶対有限差分ステップサイズ
  * `dir`: 有限差分ステップの方向
