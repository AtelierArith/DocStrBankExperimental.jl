```
checkmode(m, s::Symbol)
checkmode(m, [&, |, ==, or !], s₁::Symbol[, s₂:Symbol]...)
checkmode(f, m, [&, |, ==, or !], s₁::Symbol[, s₂:Symbol]...)
```

Tests if `m` is a `Mode` and contains the prescribed symbols.

  * In the 1st form the function tests for the presence of `s` in `m`.
  * In the 2nd form the function tests either (for `&` or if any operation symbol  is omited) that all symbols `s₁`, `s₂`, ... are in `m`, or (for `|`) that at  least one of them in `m`, or (for `==`) that `m` contains exactly the  prescribed collection of the symbols, or (for `!`) that `m` does not contain  any of the prescribed symbols.
  * In the 3rd form the function tests whether all of the symbols `s₁`, `s₂`, ...  are in `m` (also if `&` is provided). If they are –- return `f(m[s₁], m[s₂],  ...)`; if not –- return `nothing`. If `==` is also added in the function  call, the test will be positive only when `m` contains all and only the  prescribed symbols. If `!` is added in the function call, the test will be  positive only when `m` contains no any of the prescribed symbols; if that is  true, `f` is called with no arguments. Similarly for `|` – if test is true, `f` is called with no arguments.

See also: [`ArgumentModes.Mode`](@ref)

# Examples

```julia-repl
julia> m = Mode(:a => 1, :b => 2.5, :c)
Mode[==, :b => Float64, :a => Int64, :c]((a = 1, b = 2.5, c = nothing))

julia> checkmode(m, :a)
true

julia> checkmode(m, :d)
false

julia> checkmode(m, |, :a, :d)
true

julia> checkmode(m, &, :a, :d)
false

julia> checkmode(m, ==, :a, :b)
false

julia> checkmode(m, ==, :a, :b, :c)
true

julia> checkmode(m, :a) do a;  @show a   end
a = 1
1

julia> checkmode(m, :a, :b) do a, b;  @show a, b   end
(a, b) = (1, 2.5)
(1, 2.5)

julia> checkmode(m, :a, :e) do x, y;  @show x, y   end

julia> checkmode(12, :a)
false
```
