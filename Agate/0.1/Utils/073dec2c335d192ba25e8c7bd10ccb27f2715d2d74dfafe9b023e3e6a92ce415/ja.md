```
define_tracer_functions(
    parameters,
    tracers;
    auxiliary_fields=[:PAR],
    helper_functions=nothing,
    sinking_tracers=nothing,
    grid=nothing,
    open_bottom=false,
) -> DataType
```

Oceananigans.Biogeochemistry モデルタイプを作成します。

# 引数

  * `parameters`: ((<フィールド名> = <デフォルト値>, ...) の形式の値の名前付きシーケンス
  * `tracers`: (<名前> => <式>, ...) の形式の辞書

# キーワード

  * `auxiliary_fields`: 補助フィールド変数の iterable、デフォルトは `[:PAR,]`
  * `helper_functions`: トレーサー式で使用されるヘルパー関数のファイルへのオプションのパス
  * `sinking_tracers`: (正の値として渡される) 沈降速度のオプションの NamedTuple (<トレーサー名> = <速度>, ...)
  * `grid`: モデルを構築するジオメトリを定義するオプションの Oceananigans グリッドオブジェクト、`sinking_tracers` が定義されている場合は渡す必要があります
  * `open_bottom`: 沈降速度が底で滑らかにゼロに持っていかれるべきかどうかを示し、トレーサーが領域を離れるのを防ぐために、デフォルトは `true` で、これは底が開いていてトレーサーが離れることを意味します (すなわち、速度を 0 に減速することは適用されません)

`parameters` で定義されたフィールド名は、[:x, :y, :z, :t] のいずれでもあってはならず、これらは座標用に予約されており、`tracers` 式で使用されるすべてのパラメータを含む必要があります。式は、このモジュール内で定義されているメソッドまたは `helper_functions` ファイルで渡されたメソッドを使用する必要があります。

# 例

```julia
using Agate

parameters = (α=2 / 3, β=4 / 3, δ=1, γ=1)
tracers = Dict("R" => :(α * R - β * R * F), "F" => :(-γ * F + δ * R * F))
LV = define_tracer_functions(parameters, tracers)
```
