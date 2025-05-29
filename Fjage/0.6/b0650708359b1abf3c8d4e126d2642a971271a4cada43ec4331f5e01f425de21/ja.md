`@fsm` マクロは FSM の動作を定義するために使用されます。このマクロは `struct` 定義を受け取り、それを FSM の動作定義に変換します。構造体のフィールドは動作属性として扱われます。`initialstate` フィールドは FSM の初期状態を指定するために使用され、常に定義されている必要があります。FSM の動作は `FSMBehavior` 抽象型の可変サブタイプです。

`struct` 定義には、`Base.@kwdef` マクロによってサポートされる初期化を含めることができます。

# 例:

```julia
using Fjage

@states TICK TOCK

@fsm struct GrandfatherClock
  initialstate = TICK
  ticks::Int = 0
end

function Fjage.onenter(a::Agent, b::GrandfatherClock, state::typeof(TICK))
  b.ticks += 1
  @info "TICK $(b.ticks)"
  after(b, 0.5) do
    nextstate!(b, TOCK)
  end
end

function Fjage.onenter(a::Agent, b::GrandfatherClock, state::typeof(TOCK))
  @info "TOCK $(b.ticks)"
  after(b, 0.5) do
    nextstate!(b, TICK)
  end
end

function Fjage.onevent(a::Agent, b::GrandfatherClock, state, event)
  if event === :reset
    b.ticks = 0
    reenterstate(b)
  elseif event === :stop
    stop(b)
  end
end
```
