```
TapedTask(taped_globals::Any, f, args...; kwargs...)
```

Construct a `TapedTask` with the specified `taped_globals`, for function `f`, positional arguments `args`, and keyword argument `kwargs`.

# Extended Help

There are three central features of a `TapedTask`, which we demonstrate via three examples.

## Resumption

The function [`Libtask.produce`](@ref) has a special meaning in Libtask. You can insert it into regular Julia functions anywhere that you like. For example

```jldoctest tt
julia> function f()
           for t in 1:2
               produce(t)
               t += 1
           end
           return nothing
       end
f (generic function with 1 method)
```

If you construct a `TapedTask` from `f`, and call [`Libtask.consume`](@ref) on it, you'll see

```jldoctest tt
julia> t = TapedTask(nothing, f);

julia> consume(t)
1
```

The semantics of this are that [`Libtask.consume`](@ref) runs the function `f` until it reaches the call to [`Libtask.produce`](@ref), at which point it will return the argument to [`Libtask.produce`](@ref).

Subsequent calls to [`Libtask.produce`](@ref) will *resume* execution of `f` immediately after the last [`Libtask.produce`](@ref) statement that was hit.

```jldoctest tt
julia> consume(t)
2
```

When there are no more [`Libtask.produce`](@ref) statements to hit, calling [`Libtask.consume`](@ref) will return `nothing`:

```jldoctest tt
julia> consume(t)

```

## Copying

[`TapedTask`](@ref)s can be copied. Doing so creates a completely independent object. For example:

```jldoctest tt
julia> t2 = TapedTask(nothing, f);

julia> consume(t2)
1
```

If we make a copy and advance its state, it produces the same value that the original would have produced:

```jldoctest tt
julia> t3 = copy(t2);

julia> consume(t3)
2
```

Moreover, advancing the state of the copy has not advanced the state of the original, because they are completely independent copies:

```jldoctest tt
julia> consume(t2)
2
```

## TapedTask-Specific Globals

It is often desirable to permit a copy of a task and the original to differ in very specific ways. For example, in the context of Sequential Monte Carlo, you might want the only difference between two copies to be their random number generator.

A generic mechanism is available to achieve this. [`Libtask.get_taped_globals`](@ref) and [`Libtask.set_taped_globals!`](@ref) let you set and retrieve a variable which is specific to a given [`Libtask.TapedTask`](@ref). The former can be called inside a function:

```jldoctest sv
julia> function f()
           produce(get_taped_globals(Int))
           produce(get_taped_globals(Int))
           return nothing
       end
f (generic function with 1 method)
```

The first argument to [`Libtask.TapedTask`](@ref) is the value that [`Libtask.get_taped_globals`](@ref) will return:

```jldoctest sv
julia> t = TapedTask(1, f);

julia> consume(t)
1
```

The value that it returns can be changed between [`Libtask.consume`](@ref) calls:

```jldoctest sv
julia> set_taped_globals!(t, 2)

julia> consume(t)
2
```

`Int`s have been used here, but it is permissible to set the value returned by [`Libtask.get_taped_globals`](@ref) to anything you like.

# Implementation Notes

Under the hood, we implement a `TapedTask` by obtaining the `IRCode` associated to the original function, transforming it so that it implements the semantics required by the `produce` / `consume` interface, and placing it inside a `MistyClosure` to make it possible to execute.

There are two main considerations when transforming the `IRCode`. The first is to ensure that the "state" of a `TapedTask` can be copied, so that a `TapedTask` can be copied, and resumed later. The complete state of a `TapedTask` is given by its arguments, and the value associated to each ssa (these are initially undefined). To make it possible to copy the state of the ssa values, we place `Base.RefValue{T}`s into the captures of the `MistyClosure` which implements the `TapedTask`, one for each ssa in the IR (`T` is the type inferred for that ssa). A call is replaced by reading in values of ssas from these refs, applying the original operation, and writing the result to the ref associated to the instruction. For example, if the original snippet of `IRCode` is something like

```julia
%5 = f(%3, _1)
```

the transformed IR would be something like

```julia
%5 = ref_for_%3[]
%6 = f(%5, _1)
ref_for_%5[] = %6
```

Setting things up in this manner ensures that an independent copy is made by simply copying all of the refs. A `deepcopy` is required for correctness as, while the refs do not alias one another (by construction), their contents might. For example, two refs may contain the same `Array`, and in general the behaviour of a function depends on this relationship.

The second component of the transformation is implementing the `produce` mechanism, and the ability to resume computation from where we produced. Roughly speaking, the `IRCode` must be modified to ensure that whenever a `produce` call in encountered, the `MistyClosure` returns the argument to `produce`, and that subsequent calls resume computation immediately after the `produce` statement. This resumption is achieved by setting the value of a counter prior to returning following a `produce` statement – a sequence of comparisons against this counter, and [`GotoIfNot`](https://docs.julialang.org/en/v1/devdocs/ast/#Lowered-form) statement are inserted at the top of the IR. These are used to jump to the point in the code from which computation should resume. These are set up such that, when the `TapedTask` is first run, computation start froms the first statement. Observe that this is also facilitated by the ref mechanism discussed above, as it ensures that the state persists between calls to a `MistyClosure`.

The above gives the broad outline of how `TapedTask`s are implemented. We refer interested readers to the code, which is extensively commented to explain implementation details.
