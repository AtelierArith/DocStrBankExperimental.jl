```
S = Signal(val; strict_push = false)
```

Create a source `Signal` with initial value `val`, setting `strict_push` to `true` guarantees that every push to this `Signal` will be carried out independently. Otherwise if updates occur faster than what the `eventloop` can process, then only the last value before the `eventloop` kicks in will be used(*default*).

```
S = Signal(f,args...; v0 = nothing)
```

Create a derived `Signal` whos value is `f(args...)`, args can be of any type, `Signal` args get replaced by their value before calling `f(args...)`. reads best with with `do` notation(see example).if `v0` is not `nothing` then `f(args...)` will not be called directly after Signal creation instead the Signal will be initialized to have value v0.

# Syntax

```
S[] = val
```

Set the value of `S` to `val` without propogating the change to the rest of the signal graph, usefull in pull based paradigm.

```
S()
```

`pull!` Signal, pulling any changes in the Signal graph that affects `S`.

```
S(val)
```

Set the value of `S` to `val` and pushes the changes along the Signal graph.

```
S[]
```

Get the current value stored in `S` without pulling changes from the graph.

# Examples

```
julia> A = Signal(1) # source Signal
Signal
value: 1

julia> B = 2 # non-Signal input
2

julia> C = Signal(A, B) do a, b # derived Signal
           a + b
       end

Signal
value: 3

julia> A[] = 10 # set value without propogation
10
julia> C[] # reads current value
3
julia> C() # pull latest changes from the Signal graph
12
julia> A(100) # set value to a signal and propogate this change
100
julia> C[]
102
```
