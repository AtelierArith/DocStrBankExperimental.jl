```
@fix_show constructor::T
```

`constructor(args...; kwargs...)` の形を持つすべてのオブジェクトの人間が読みやすい表示を得るために `Base.show` をオーバーロードします。ここで、これらのオブジェクトの型の上限を `T` とし、他のオブジェクトのスーパタイプではないものとします。

# 例

次のようなコンストラクタ `LP` の定義を考えます：

```julia
import StatisticalMeasuresBase as API
using StatisticalMeasuresBase

struct LPOnScalars{T}
    p::T
end
measure(yhat, y) = abs(yhat - y)^measure.p

LP(; p=2) = multimeasure(LPOnScalars(p))

julia> LP()
multimeasure(LPOnScalars{Int64}(2))
```

これを次のように修正します：

```julia
LPType = API.Multimeasure{<:LPOnScalars}
@fix_show LP::LPType

julia> LP()
LP(
  p = 2)
```
