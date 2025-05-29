```
Advice{func, context} <: Function
```

Advices allow for composable, highly flexible modifications of data by encapsulating a function call. They are inspired by elisp's advice system, namely the most versatile form — `:around` advice, and Clojure's advisors.

A `Advice` is essentially a function wrapper, with a `priority::Int` attribute. The wrapped functions should be of the form:

```julia
(action::Function, args...; kargs...) ->
  ([post::Function], action::Function, args::Tuple, [kargs::NamedTuple])
```

Short-hand return values with `post` or `kargs` omitted are also accepted, in which case default values (the `identity` function and `(;)` respectively) will be automatically substituted in.

```
    input=(action args kwargs)
         ┃                 ┏╸post=identity
       ╭─╂────advisor 1────╂─╮
       ╰─╂─────────────────╂─╯
       ╭─╂────advisor 2────╂─╮
       ╰─╂─────────────────╂─╯
       ╭─╂────advisor 3────╂─╮
       ╰─╂─────────────────╂─╯
         ┃                 ┃
         ▼                 ▽
action(args; kargs) ━━━━▶ post╺━━▶ result
```

To specify which transforms a Advice should be applied to, ensure you add the relevant type parameters to your transducing function. In cases where the transducing function is not applicable, the Advice will simply act as the identity function.

After all applicable `Advice`s have been applied, `action(args...; kargs...) |> post` is called to produce the final result.

The final `post` function is created by rightwards-composition with every `post` entry of the advice forms (i.e. at each stage `post = post ∘ extra` is run).

The overall behaviour can be thought of as *shells* of advice.

```
        ╭╌ advisor 1 ╌╌╌╌╌╌╌╌─╮
        ┆ ╭╌ advisor 2 ╌╌╌╌╌╮ ┆
        ┆ ┆                 ┆ ┆
input ━━┿━┿━━━▶ function ━━━┿━┿━━▶ result
        ┆ ╰╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╯ ┆
        ╰╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╯
```

# Constructors

```julia
Advice(priority::Int, f::Function)
Advice(f::Function) # priority is set to 1
```

# Examples

**1. Logging every time a DataSet is loaded.**

```julia
loggingadvisor = Advice(
    function(post::Function, f::typeof(load), loader::DataLoader, input, outtype)
        @info "Loading $(loader.data.name)"
        (post, f, (loader, input, outtype))
    end)
```

**2. Automatically committing each data file write.**

```julia
writecommitadvisor = Advice(
    function(post::Function, f::typeof(write), writer::DataWriter{:filesystem}, output, info)
        function writecommit(result)
            run(`git add $output`)
            run(`git commit -m "update $output"`)
            result
        end
        (post ∘ writecommit, writefn, (output, info))
    end)
```
