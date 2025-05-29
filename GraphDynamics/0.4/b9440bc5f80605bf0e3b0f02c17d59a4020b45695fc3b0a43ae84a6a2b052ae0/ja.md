computed_properties(::Subsystem{T}) :: NamedTuple{props, NTuple{N, funcs}}

サブシステムが既存のプロパティに基づいてオンザフライで計算できるプロパティを持っていることを示します。ModelingToolkit.jlで使用される用語では、これらは「観測状態」と呼ばれます。

この関数は`Subsystem`を受け取り、各キーが計算可能なプロパティ名であり、各値がサブシステムを受け取り計算された値を返す関数である`NamedTuple`を返します。

デフォルトでは、この関数は空のNamedTupleを返します。

例:

```julia
struct Position end
function GraphDynamics.computed_properties(::Subsystem{Position})
    (;r = (;x, y) -> √(x^2 + y^2),
      θ = (;x, y) -> atan(y, x))
end

let sys = Subsystem{Position}(states=(x=1, y=2), params=(;))
    sys.r == √(sys.x^2 + sys.y^2)
end
```
