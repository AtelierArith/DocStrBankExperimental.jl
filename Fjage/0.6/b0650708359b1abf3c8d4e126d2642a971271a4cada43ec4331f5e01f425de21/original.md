The `@fsm` macro is used to define a FSM behavior. The macro takes in a `struct` definition and converts it into an FSM behavior definition. The fields in the struct are treated as behavior attributes. The `initialstate` field is used to specify the initial state of the FSM, and must always be defined. FSM behaviors are mutable subtypes of the `FSMBehavior` abstract type.

The `struct` definition may include initialization, as supported by the `Base.@kwdef` macro.

# Example:

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
