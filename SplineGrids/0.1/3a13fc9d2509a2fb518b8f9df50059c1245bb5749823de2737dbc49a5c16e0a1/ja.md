```
SplineDimension(
    n_basis_functions::Integer,
    degree::Integer,
    n_sample_points::Integer;
    max_derivative_order::Integer = 0,
    knot_vector::Union{Nothing, KnotVector{Tv, Ti}} = nothing,
    backend::Backend = CPU(),
    float_type::Type{Tv} = Float32,
    int_type::Type{Ti} = Int32,
    kwargs...)::SplineDimension where {Tv <: AbstractFloat, Ti <: Integer}
```

SplineDimensionのコンストラクタ。オプションで`knot_vector`キーワード引数を渡すことができ、そうでない場合はデフォルトのノットベクトルが生成されます。現時点では、デフォルトでサンプルポイントはノットベクトルの範囲に均等に配置されています。キーワード引数はKnotVectorコンストラクタに渡されます。

## 入力

  * `n_basis_functions`: このスプライン次元の基底関数の数
  * `degree`: このスプライン次元の基底関数の次数
  * `n_sample_points`: 基底関数の定義域がサンプリングされる点の数
  * `max_derivative_order`: `evaluate!`で計算される基底関数の最大導関数の次数。デフォルトは`0`。`knot_vector`: 基底関数が定義されるノットベクトル。デフォルトは`nothing`で、これはデフォルトのクランプ/オープン均等間隔のノットベクトルが定義されることを意味します。
  * `backend`: オブジェクト内の配列のKernelAbstractionsバックエンド。デフォルトは`CPU()`。注意: ノットベクトルが提供される場合、そのバックエンドが優先されます。
  * `float_type`: すべての浮動小数点配列の型。デフォルトは`Float32`。
