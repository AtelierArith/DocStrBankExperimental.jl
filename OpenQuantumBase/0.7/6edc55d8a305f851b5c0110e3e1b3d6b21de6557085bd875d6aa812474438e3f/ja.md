```julia
struct SparseHamiltonian{T<:Number, dimensionless_time} <: OpenQuantumBase.AbstractHamiltonian{T<:Number}
```

時間依存ハミルトニアンオブジェクトをスパース行列で定義します。

# フィールド

  * `f`: 時間依存関数のリスト
  * `m`: 定数行列のリスト
  * `u_cache`: 内部キャッシュ
  * `size`: サイズ
