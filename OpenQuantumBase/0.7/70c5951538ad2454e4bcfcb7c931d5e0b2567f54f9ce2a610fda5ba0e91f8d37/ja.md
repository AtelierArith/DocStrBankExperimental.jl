```julia
struct DenseHamiltonian{T<:Number, dimensionless_time} <: OpenQuantumBase.AbstractDenseHamiltonian{T<:Number}
```

時間依存ハミルトニアンオブジェクトをJulia配列を使用して定義します。

# フィールド

  * `f`: 時間依存関数のリスト
  * `m`: 定数行列のリスト
  * `u_cache`: 内部キャッシュ
  * `size`: サイズ
