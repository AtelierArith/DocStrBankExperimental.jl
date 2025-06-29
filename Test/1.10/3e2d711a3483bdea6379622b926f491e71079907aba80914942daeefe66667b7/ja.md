```
@inferred [AllowedType] f(x)
```

呼び出し式 `f(x)` がコンパイラによって推論されたのと同じ型の値を返すことをテストします。型の安定性を確認するのに役立ちます。

`f(x)` は任意の呼び出し式であり、型が一致する場合は `f(x)` の結果を返し、異なる型が見つかった場合は `Error` `Result` を返します。

オプションで、`AllowedType` はテストを緩和し、`f(x)` の型が推論された型と `AllowedType` の剰余で一致する場合、または戻り値の型が `AllowedType` のサブタイプである場合にテストを通過させます。これは、`Union{Nothing, T}` や `Union{Missing, T}` のような小さな和集合を返す関数の型の安定性をテストする際に便利です。

```jldoctest; setup = :(using InteractiveUtils), filter = r"begin\n(.|\n)*end"
julia> f(a) = a > 1 ? 1 : 1.0
f (generic function with 1 method)

julia> typeof(f(2))
Int64

julia> @code_warntype f(2)
MethodInstance for f(::Int64)
  from f(a) @ Main none:1
Arguments
  #self#::Core.Const(f)
  a::Int64
Body::UNION{FLOAT64, INT64}
1 ─ %1 = (a > 1)::Bool
└──      goto #3 if not %1
2 ─      return 1
3 ─      return 1.0

julia> @inferred f(2)
ERROR: return type Int64 does not match inferred return type Union{Float64, Int64}
[...]

julia> @inferred max(1, 2)
2

julia> g(a) = a < 10 ? missing : 1.0
g (generic function with 1 method)

julia> @inferred g(20)
ERROR: return type Float64 does not match inferred return type Union{Missing, Float64}
[...]

julia> @inferred Missing g(20)
1.0

julia> h(a) = a < 10 ? missing : f(a)
h (generic function with 1 method)

julia> @inferred Missing h(20)
ERROR: return type Int64 does not match inferred return type Union{Missing, Float64, Int64}
[...]
```
