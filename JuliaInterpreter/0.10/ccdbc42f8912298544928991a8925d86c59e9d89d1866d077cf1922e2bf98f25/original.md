```
ExprSplitter(mod::Module, ex::Expr; lnn=nothing)
```

Given a module `mod` and a top-level expression `ex` in `mod`, create an iterable that returns individual expressions together with their module of evaluation. Optionally supply an initial `LineNumberNode` `lnn`.

# Example

In a fresh session,

```
julia> expr = quote
           public_fn(x::Integer) = true
           module Private
           private(y::String) = false
           end
           const threshold = 0.1
       end;

julia> for (mod, ex) in ExprSplitter(Main, expr)
           @show mod ex
       end
mod = Main
ex = quote
    #= REPL[7]:2 =#
    public_fn(x::Integer) = begin
            #= REPL[7]:2 =#
            true
        end
end
mod = Main.Private
ex = quote
    #= REPL[7]:4 =#
    private(y::String) = begin
            #= REPL[7]:4 =#
            false
        end
end
mod = Main
ex = :($(Expr(:toplevel, :(()), :(const threshold = 0.1))))
```

`ExprSplitter` created `Main.Private` was created for you so that its internal expressions could be evaluated. `ExprSplitter` will check to see whether the module already exists and if so return it rather than try to create a new module with the same name.

In general each returned expression is a block with two parts: a `LineNumberNode` followed by a single expression. In some cases the returned expression may be `:toplevel`, as shown in the `const` declaration, but otherwise it will preserve its parent's `head` (e.g., `expr.head`).

# World age, frame creation, and evaluation

The primary purpose of `ExprSplitter` is to allow sequential return to top-level (e.g., the REPL) after evaluation of each expression. Returning to top-level allows the world age to update, and hence allows one to call methods and use types defined in earlier expressions in a block.

For evaluation by JuliaInterpreter, the returned module/expression pairs can be passed directly to the `Frame` constructor. However, some expressions cannot be converted into `Frame`s and may need special handling:

```julia
julia> for (mod, ex) in ExprSplitter(Main, expr)
           if ex.head === :global
               # global declarations can't be lowered to a CodeInfo.
               # In this demo we choose to evaluate them, but you can do something else.
               Core.eval(mod, ex)
               continue
           end
           frame = Frame(mod, ex)
           debug_command(frame, :c, true)
       end

julia> threshold
0.1

julia> public_fn(3)
true
```

If you're parsing package code, `ex` might be a docstring-expression; you may wish to check for such expressions and take distinct actions.

See [`Frame(mod::Module, ex::Expr)`](@ref) for more information about frame creation.
