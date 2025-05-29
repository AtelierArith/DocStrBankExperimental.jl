```
@public name₁ name₂ … nameₙ
@public @macroname
```

Declare public API names for the current module.

The second form `@public @macroname` is equivalent to `@public var"@macroname"`.

# Extended help

Note that where this macro is invoked is important. Consider:

```julia
module A1
    using PublicAPI: @public
    @public B, C
    module B
        f() = nothing
    end
    module C
        using PublicAPI: @public
        using ..B: f
        @public f
    end
end
```

and

```julia
module A2
    using PublicAPI: @public
    @public B, C
    module B
        using PublicAPI: @public
        f() = nothing
        @public f
    end
    module C
        using ..B: f
    end
end
```

The fully-qualified names `A1.C.f` and `A2.B.f` are public but `A1.B.f` and `A2.C.f` are private.
