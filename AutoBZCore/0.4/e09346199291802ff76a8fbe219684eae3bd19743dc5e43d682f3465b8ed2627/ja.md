```
load_bz(bz::AbstractBZ, [T::Type=Float64])
load_bz(bz::AbstractBZ, A::AbstractMatrix, [B::AbstractMatrix])
```

ブリルアンゾーンを読み込むためのインターフェース。

## 引数

  * `bz::AbstractBZ`: 構築するブリルアンゾーンの種類、例: [`FBZ`](@ref) または [`IBZ`](@ref)
  * `T::Type`: ドメインの精度を設定する数値型（デフォルト: `Float64`）
  * `A::AbstractMatrix`: $d \times d$ 行列で、列は $d$ 次元結晶の実空間格子ベクトル
  * `B::AbstractMatrix`: $d \times d$ 行列で、列は $d$ 次元ブリルアンゾーンの逆空間格子ベクトル（デフォルト: `A' \ 2πI`）

!!! note "仮定"
    `AutoBZCore` は、すべての計算が逆格子基底で行われると仮定しています。なぜなら、それがワニエ補間子が最も効率的に記述される基底だからです。詳細については [`SymmetricBZ`](@ref) を参照してください。また、被積分関数が評価するのが安価であると仮定しているため、最初から適応的な手法を提供し、戻り値の型を実行時に決定できるようにしています（コンパイル時にもメカニズムが整っています）。

