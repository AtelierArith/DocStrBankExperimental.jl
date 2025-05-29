`@usingmerge [reexport] [verbose=true] SomeModule[: symbol1, symbol2...]`

do  `using` module `SomeModule`, in addition merging all method definitions (or  `using` from  `SomeModule` methods  definitions `symbol1, symbol2...`) exported  by  `SomeModule`  with  methods  of  the same name in the current module.

If  `reexport` is given all  new names (non-conflicting with  a name in the current  module)  exported  from  `SomeModule`  are  (re-)exported from the current  module. If a  name is not  new it is  assumed that the decision to export it or not has been taken before.

If `verbose=true` conflicting methods are printed. If `verbose=2` every executed command is printed before execution. If `verbose=3` boths happens.

If  a name exported  by `SomeModule` conflicts  with a name  which is not a method a warning is printed and the name is not merged (not imported).

An example of use:

```julia
julia> using UsingMerge

julia> foo(x::Int)=2
foo (generic function with 1 method)

julia> module Bar
       export foo
       foo(x::Float64)=3
       end
Main.Bar

julia> @usingmerge verbose=3 Bar
# Bar.foo conflicts with Main.foo --- adding methods
Main.foo(x::Float64) = Bar.foo(x)
```

One  could have done `@usingmerge Bar:  foo` to import/merge `foo` only. In any  case, note that the equivalent of `using  Bar: Bar` is done in any case to put the name `Bar` in scope.
