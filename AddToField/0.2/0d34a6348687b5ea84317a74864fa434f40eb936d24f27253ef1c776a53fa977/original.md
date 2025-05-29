```
@addto!(x, body)
```

Set properties or indices of `x` using `@add` statments inside `body`.

### Usage

Within `body`, you can add properies or indices of `x` with the following.

  * `@add x`: The named tuple will contain the field `:x` with the value of `x`.
  * `@add x, y, z`: The named tuple will contain the fields `x`, `y`, and `z`  with their corresponding values.
  * `@add x = expr`: The named tuple will contain the field `:x` with the value of  `expr`. The variable `x` will still be created.
  * `@add "My value" x`: The named tuple will contain the field `Symbol("My value)`  with the value of `x`. You can also interpolate values inside the `String`  name.
  * `@add "My value" x = expr`: The named tuple will contain the field  `Symbol("My value")` with the value of `expr`. The variable `x` will still be created.

`@addto!` defaults to calling `setproperty!` on `x`. However with `AbstractDict`, it calls `setindex!` with `Symbol`s. Wieh `AbstractDict{<:AbstractString}` is calls `setindex!` with `String`s.

`@addto! d begin ... end` does not create a new scope, meaning changes all variable assignments in the inside the expression modify the existing scope. To create a new scope, use `@addto! d let ... end`.

### Example:

```jldoctest
julia> D = Dict();

julia> s = "My long name";

julia> res = @addto! D begin
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
Dict{Any,Any} with 8 entries:
  :a                     => 1
  :f                     => 6
  :b                     => 2
  :h                     => 8
  :g                     => 7
  :d1                    => 4
  :c1                    => 3
  Symbol("My long name") => 5

julia> @addto! d let
           @add local_var = 500
       end;

julia> isdefined(Main, :local_var)
false
```

!!! note
    `You` cannot use `@addto!` in new scopes created with `body`. The following will fail

    ```julia
    @addto! D begin
    	let
    	    a = 1
    	    @add a
    	end
    end
    ```

    This is because `@addto!` creates anonymous variables, then constructs the `setproperty!` or `setindex!` calls at the end of the expression.

