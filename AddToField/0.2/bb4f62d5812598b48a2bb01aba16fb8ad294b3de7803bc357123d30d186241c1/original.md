```
@addnt(body)
```

Create a named tuple using `@add` statments inside `body`.

### Usage

Within `body`, you can create a namedtuple with the following syntaxes.

  * `@add x`: The named tuple will contain the field `:x` with the value of `x`.
  * `@add x, y, z`: The named tuple will contain the fields `x`, `y`, and `z` with  their corresponding values.
  * `@add x = expr`: The named tuple will contain the field `:x` with the value of  `expr`. The variable `x` will still be created.
  * `@add "My value" x`: The named tuple will contain the field `Symbol("My value)`  with the value of `x`. You can also interpolate values inside the `String`  name.
  * `@add "My value" x = expr`: The named tuple will contain the field  `Symbol("My value")` with the value of `expr`. The variable `x` will still be created.

`@addnt begin ... end` does not create a new scope, meaning changes all variable assignments in the inside the expression modify the existing scope. To create a new scope, use `@addnt let ... end`.

### Example:

```jldoctest
julia> s = "My long name";

julia> res = @addnt begin
		a = 1
		@add a

		f, g, h = 6, 7, 8
		@add f, g, h

		@add b = 2
		@add :c1 c = 3
		@add "d1" d = 4
		@add "My long name" e = 5
	end
end
(a = 1, f = 6, g = 7, h = 8, b = 2, c1 = 3, d1 = 4, My long name = 5)

julia> @addnt let
           @add local_var = 500
       end
(local_var = 500,)

julia> isdefined(Main, :local_var)
false
```

!!! note
    `You` cannot use `@add` in new scopes created with `body`. The following will fail

    ```julia
    @addnt begin
    	let
    	    a = 1
    	    @add a
    	end
    end
    ```

    This is because `@addnt` creates anonymous variables, then constructs the named tuple at the end of the expression. The same applies for `for` loops and `function`s inside the `@addnt` and `@addto!` blocks.

