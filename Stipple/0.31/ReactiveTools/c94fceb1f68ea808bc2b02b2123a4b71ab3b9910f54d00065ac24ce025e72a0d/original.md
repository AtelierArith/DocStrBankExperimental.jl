```
@handler App expr
```

Defines a handler function that can be called from within a ReactiveModel App, if not present, the macro will add the variable `__model__` as the first argument.

Parameters:

  * `App`: either

      * a ReactiveModel (e.g. `MyApp`)
      * a list of reactive variables (e.g. `(:r1, :r2)`)
      * a tuple or vector of a list of reactive variables and a list of non-reactive variables (e.g. `((:r,), (:nr,))`)
  * `expr`: function definition, e.g. `function my_handler() println("n: $n") end`

### Example 1

```julia
@app MyApp begin
  @in i = 0
  @onchange i on_i()
    println("Hello World")
  end
end

@handler MyApp function on_i()
  println("i: $i")
end
```

### Example 2

```julia-repl
julia> @macroexpand @handler (:a,) function f() a end
quote
    function f(__model__)
        model.a[]
    end
end

julia> @macroexpand @handler ((:a,), (:b,)) function f(x, __model__) a, b end
quote
    function f(x, __model__)
        (__model__.a[], __model__.b)
    end
end
```
