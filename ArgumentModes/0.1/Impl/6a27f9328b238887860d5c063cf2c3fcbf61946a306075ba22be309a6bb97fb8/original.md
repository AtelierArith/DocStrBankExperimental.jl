```
struct Mode
```

`Mode` could be seen as an extension of `Val` and is intended to be used as  a type for a function argument. Its semantics is a set of symbols (flags) whose  value is taken into account during method dispatch. A specialization of `Mode`   allows to declare a list of symbols which a function method would accept for  the argument. The symbols could be accompanied with additional parameters with  prescribed types.

Here is a more detailed description of the mechanics of the type. A specialized  `Mode` type **M=Mode[s₁⇒t₁, s₂⇒t₂, ...]** is determined by a collection of  symbols **s₁**, **s₂**, ...  of type `Symbol` and corresponding types **t₁**,  **t₂**, ... (of type `DataType` or `Union` of `DataType`s). An instance  **m::Mode** of `Mode` additionally contains values **vᵢ** for each **sᵢ** of  type **tᵢ**. Let **param(x)** denote the collection **{sᵢ=>tᵢ}ᵢ** of **x**  (here **x** is an instance or a specialized type of `Mode`). Then **m** is of  type **M** only if **param(m) ⊆ param(M)**. This allows the dispatch to choose  an appropriate method of a function based on **param(m)**.

See also: [`checkmode`](@ref)

# Constructor of the type specialization

```
Mode[ s₁ [=> t₁] [, s₂ [=> t₂]]... ]
```

Construct a specialization **M=Mode[s₁⇒t₁, s₂⇒t₂, ...]** to be used as a  type for a argument in a function method declaration. The argument with type  **M** would accept only instances **m::Mode** with **param(m) ⊆ param(M)**.  Some or all **tᵢ** may absent in the type declaration which defaults to  `Nothing`. An example: `Mode[:a, :b => Int, :c => Tuple{Int, String}]`.

Symbol `==` could also be added as the first argument in a constructor call to indicate that the concrete type is wanted (not an `UnionAll` as above). This option is added only for auxiliary purposes and generally should not be useful.

Note that such nonconventional syntax with brackets `[`,`]` is used to make the  code for a type declaration look similar to the presentation of the type name  in a function signature.

# Constructors of an instance

```
Mode( s₁[=> v₁] [, s₂ [=> v₂]]... )
```

Construct an instance **m::Mode[s₁⇒typeof(v₁), s₂⇒typeof(v₂), ...]** with values **v₁, v₂, ...**. Some or all of **vᵢ** might be omited which defaults to  `nothing`. An example: `Mode(:a => 25, :b, :c => "Hello world!")`.

```
Mode(s)
```

Construct an instance **m::Mode[s⇒Nothing]** with `nothing` value. The  type and value could be set by a subsequent call **m**`=>`**v**. Several  instances could be joined with `~` operator. For example, `Mode(:a)=> 25 ~ Mode (:b) ~ Mode(:c)=> "Hello world!"` is equivalent to `Mode(:a => 25, :b, :c =>  "Hello world!")`.

# Operations on an instance

Let **m, m₁, m₂::Mode**. Then

  * `m => v` given `m::Mode[s => Nothing]`: return a new instance with symbol  **s** having value and type of `v`.
  * `m₁ ~ m₂`: join `m₁` and `m₂`. Throws an ArgumentError if `m₁` and `m₂`  contain the same symbols.
  * `keys(m), values(m), pairs(m)`: return symbols / values / pairs of symbols  and values.
  * `m[s₁ [, s₂]... ]` for `sᵢ::Symbol`: return the value of `s₁` / tuple of  values of `s₁, s₂, ...`.
  * `m[]`: if `m` contains only one value, return it; throw an ArgumentError  otherwise
  * `checkmode(m, ...)`: check if `m` is a `Mode` and contains the prescribed   symbols, and, possibly, do an action. See [`ArgumentModes.checkmode`](@ref)  for detailed description.

# Examples

### 1. Usage in function declarations and calls

```julia-repl
julia> f(x) = println("Anything: $x")
       f(x::Mode[:iterator => Any]) = println("Values from iterator: $(x[]...)")
       f(x::Mode[:fromargs], y...) = println("Fromargs: $(y...)")
       function f(x::Union{Int, Mode[:a, :b, :c => Int]})
           checkmode(x, :a) do _;  println(":a")  end
           checkmode(x, :c) do c;  println(":c = $c")  end
           checkmode(x, :b) && println(":b")
           if x isa Int;  println("x = $x") end
       end
f (generic function with 4 methods)

julia> methods(f)
# 4 methods for generic function "f":
[1] f(x::Mode[:iterator => Any]) in Main at REPL[34]:1
[2] f(x::Mode[:fromargs], y...) in Main at REPL[36]:1
[3] f(x::Union{Int64, Mode[:c => Int64, :a, :b]}) in Main at REPL[38]:1
[4] f(x) in Main at REPL[33]:1

julia> f(25.0)
Anything: 25.0

julia> f(Mode(:iterator)=> 1:5)
Values from iterator: 12345

julia> f(Mode(:fromargs), 1, 2, 3, 4, 5)
Fromargs: 12345

julia> f(1)
x = 1

julia> f(Mode(:a, :c => 125))
:a
:c = 125

julia> f(Mode(:fromargs, :iterator => 1:5), 2)
ERROR: MethodError: no method matching f(::Mode[==, :iterator => UnitRange, :fromargs], ::Int64)
Closest candidates are:
  f(::Mode[:fromargs], ::Any...) at REPL[36]:1
  f(::Any) at REPL[33]:1
Stacktrace:
 [1] top-level scope
   @ REPL[59]:1

```

### 2. Construction of types and instances, operations on an instance

```julia-repl
julia> M = Mode[:a => Real, :b => Union{Number, String}, :c]
Mode[:a => Real, :b => Union{Number, String}, :c]

julia> m1 = Mode(:a => 2.5, :c)
Mode[==, :a => Float64, :c]((a = 2.5, c = nothing))

julia> m1 isa M
true

julia> m2 = Mode(:a)=> 2.5 ~ Mode(:c)
Mode[==, :a => Float64, :c]((a = 2.5, c = nothing))

julia> m1 === m2
true

julia> Mode(:a => 2.5, :c, :d) isa M
false

julia> Mode(:a => "2", :c) isa M
false

julia> Mode(:a => 2.5, :c) ~ Mode(:b)=> "Hello world!"
Mode[==, :a => Float64, :c, :b => String]((a = 2.5, b = "Hello world!", c = nothing))

julia> Mode(:a => 2.5, :c) ~ Mode(:b)=> "Hello world!" ~ Mode(:a)=> 2
ERROR: ArgumentError: Duplicated keys :a

julia> checkmode(m, :a)
true

julia> checkmode(m, &, :a, :b, :g)
false

julia> checkmode(m, |, :a, :b, :g)
true

julia> m[:a, :c]
(2.5, nothing)

julia> m2 = Mode(:a => 2.5)
Mode[:a => Float64]((a = 2.5,))

julia> m2[]
2.5
```

# Notes

  * `show` is redefined for the `DataType` of `Mode` for more compact and  pleasent presentation of **s⇒t** pairs declared in the type. The actual  signature of the type is `struct ArgnmentModes.Mode{NameType,  ValuesNamedTuple}` where `NameType` containes all pairs **s⇒t** and  `ValuesNamedTuple` contains `NamedTuple` for storing the actual values  associated with the symbols.
