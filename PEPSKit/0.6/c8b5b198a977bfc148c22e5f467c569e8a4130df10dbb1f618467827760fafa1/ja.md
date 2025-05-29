```julia
struct LocalOperator{T<:Tuple, S}
```

格子上で作用する局所演算子の和。格子はベクトル空間の行列として保存され、項はインデックスと演算子のペアのタプルとして保存されます。

## フィールド

  * `lattice::Matrix{S}`: 演算子が作用する格子。
  * `terms::T`: インデックスと演算子のペアのタプルとして保存された演算子の項。

## コンストラクタ

```
LocalOperator(lattice::Matrix{S}, terms::Pair...)
LocalOperator{T,S}(lattice::Matrix{S}, terms::T) where {T,S}
```

## 例

```julia
lattice = fill(ℂ^2, 1, 1) # 単一サイトユニットセル
O1 = LocalOperator(lattice, ((1, 1),) => σx, ((1, 1), (1, 2)) => σx ⊗ σx, ((1, 1), (2, 1)) => σx ⊗ σx)
```
