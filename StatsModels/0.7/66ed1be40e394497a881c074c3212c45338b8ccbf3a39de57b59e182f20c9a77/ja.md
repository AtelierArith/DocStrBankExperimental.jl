```
InteractionTerm{Ts} <: AbstractTerm
```

二つ以上の個別の項の*相互作用*を表します。

複数の `AbstractTerm` を `&` で組み合わせることによって生成されます（これは `@formula` 内の `&` への呼び出しが下に降りるものです）。

# フィールド

  * `terms::Ts`: 相互作用に参加する項。

# 例

```jldoctest
julia> using StableRNGs; rng = StableRNG(1);

julia> d = (y = rand(rng, 9), a = 1:9, b = rand(rng, 9), c = repeat(["d","e","f"], 3));

julia> t = InteractionTerm(term.((:a, :b, :c)))
a(unknown) & b(unknown) & c(unknown)

julia> t == term(:a) & term(:b) & term(:c)
true

julia> t = apply_schema(t, schema(d))
a(continuous) & b(continuous) & c(DummyCoding:3→2)

julia> modelcols(t, d)
9×2 Matrix{Float64}:
 0.0       0.0
 1.88748   0.0
 0.0       1.33701
 0.0       0.0
 0.725357  0.0
 0.0       0.126744
 0.0       0.0
 4.93994   0.0
 0.0       4.33378

julia> modelcols(t.terms, d)
([1, 2, 3, 4, 5, 6, 7, 8, 9], [0.236781883208121, 0.9437409715735081, 0.4456708824294644, 0.7636794266904741, 0.14507148958283067, 0.021124039581375875, 0.15254507694061115, 0.617492416565387, 0.48153065407402607], [0.0 0.0; 1.0 0.0; … ; 1.0 0.0; 0.0 1.0])
```
