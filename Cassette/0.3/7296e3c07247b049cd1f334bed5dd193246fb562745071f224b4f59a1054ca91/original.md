```
overdub(context::Context, f, args...)
```

Execute `f(args...)` overdubbed with respect to `context`.

More specifically, execute `f(args...)`, but with every internal method invocation `g(x...)` replaced by statements similar to the following:

```
begin
    prehook(context, g, x...)
    overdub(context, g, x...) # %n
    posthook(context, %n, g, x...)
    %n
end
```

Otherwise, if Cassette cannot retrieve lowered IR for the method body of `f(args...)`, then `fallback(context, f, args...)` will be called instead. Cassette's [`canrecurse`](@ref) function is a useful utility for checking if this will occur.

If the injected `prehook`/`posthook` statements are not needed for your use case, you can disable their injection via the [`disablehooks`](@ref) function.

Additionally, for every method body encountered in the execution trace, apply the compiler pass associated with `context` if one exists. Note that this user-provided pass is performed on the method IR before method invocations are transformed into the form specified above. See the [`@pass`](@ref) macro for further details.

If `Cassette.hastagging(typeof(context))`, then a number of additional passes are run in order to accomodate tagged value propagation:

  * `Expr(:new)` is replaced with a call to `Cassette.tagged_new`
  * `Expr(:splatnew)` is replaced with a call to `Cassette.tagged_splatnew`
  * conditional values passed to `Expr(:gotoifnot)` are untagged
  * arguments to `Expr(:foreigncall)` are untagged
  * load/stores to external module bindings are intercepted by the tagging system

The default definition of `overdub` is to recursively enter the given function and continue overdubbing, but one can interrupt/redirect this recursion by overloading `overdub` w.r.t. a given context and/or method signature to define new contextual execution primitives. For example:

```
julia> using Cassette

julia> Cassette.@context Ctx;

julia> Cassette.overdub(::Ctx, ::typeof(sin), x) = cos(x)

julia> Cassette.overdub(Ctx(), x -> sin(x) + cos(x), 1) == 2 * cos(1)
true
```

See also: [`recurse`](@ref), [`prehook`](@ref), [`posthook`](@ref)
