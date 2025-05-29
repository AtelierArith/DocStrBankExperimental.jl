Macro that transforms a function definition in a finite-state machine:

  * Defines a new `mutable struct` that implements the iterator interface and is used to store the internal state.
  * Makes this new type callable having following characteristics:

      * implementents the statements from the initial function definition but;
      * returns at a `@yield` statement and;
      * continues after the `@yield` statement when called again.
  * Defines a constructor function that respects the calling conventions of the initial function definition and returns an object of the new type.

If the element type and length is known, the resulting iterator can be made more efficient as follows:

  * Use `length=ex` to specify the length (if known) of the iterator, like:   @resumable length=ex function f(x); body; end Here `ex` can be any expression containing the arguments of `f`.
  * Use `function f(x)::T` to specify the element type of the iterator.

# Extended

```julia
julia> @resumable length=n^2 function f(n)::Int
         for i in 1:n^2
           @yield i
         end
       end
f (generic function with 2 methods)

julia> collect(f(3))
9-element Vector{Int64}:
 1
 2
 3
 4
 5
 6
 7
 8
 9
```
