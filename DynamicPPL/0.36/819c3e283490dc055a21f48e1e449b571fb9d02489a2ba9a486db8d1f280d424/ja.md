```
unfix(model::Model)
unfix(model::Model, variables...)
```

`variables...` が *固定されていない* `Model` を返します。`variables` が提供されていない場合、現在固定されているすべての変数はもはや固定されなくなります。

これは本質的に [`fix`](@ref) の逆です。これは同様の制限を受けることも意味します。

現在、`variables` は `fix` に提供された明示的な値を取ることのみをサポートしています。

# 例

```jldoctest unfix
julia> using Distributions

julia> @model function demo()
           m ~ Normal()
           x ~ Normal(m, 1)
           return (; m=m, x=x)
       end
demo (generic function with 2 methods)

julia> fixed_model = fix(demo(), m = 1.0, x = 10.0);

julia> fixed_model()
(m = 1.0, x = 10.0)

julia> # `VarName` を指定して `unfix` することによって。
       model = unfix(fixed_model, @varname(m));

julia> (m, x) = model(); (m ≠ 1.0 && x == 10.0)
true

julia> # `NamedTuple` が基盤として使用されている場合、シンボルを直接提供することもできます
       # （ただし、変数がコンパイル時に知られている場合は `@varname` アプローチが好ましいです）。
       model = unfix(fixed_model, :m);

julia> (m, x) = model(); (m ≠ 1.0 && x == 10.0)
true

julia> # 一度に複数の `unfix`:
       (m, x) = unfix(model, :m, :x)(); (m ≠ 1.0 && x ≠ 10.0)
true

julia> # シンボルなしで `unfix` すると、すべての変数が `unfix` されます。
       (m, x) = unfix(model)(); (m ≠ 1.0 && x ≠ 10.0)
true

julia> # 可能であればコンパイル時に `unfix` を実行するための `Val` の使用もサポートされています。
       model = unfix(fixed_model, Val{:m}());

julia> (m, x) = model(); (m ≠ 1.0 && x == 10.0)
true
```

同様に `Dict` を使用する場合:

```jldoctest unfix
julia> fixed_model_dict = fix(demo(), @varname(m) => 1.0, @varname(x) => 10.0);

julia> fixed_model_dict()
(m = 1.0, x = 10.0)

julia> unfixed_model_dict = unfix(fixed_model_dict, @varname(m));

julia> (m, x) = unfixed_model_dict(); m ≠ 1.0 && x == 10.0
true
```

しかし、前述のように、`unfix` は以前に `fix` に明示的に提供された変数にのみサポートされています:

```jldoctest unfix
julia> @model function demo_mv(::Type{TV}=Float64) where {TV}
           m = Vector{TV}(undef, 2)
           m[1] ~ Normal()
           m[2] ~ Normal()
           return m
       end
demo_mv (generic function with 4 methods)

julia> model = demo_mv();

julia> fixed_model = fix(model, @varname(m) => [1.0, 2.0]);

julia> fixed_model()
2-element Vector{Float64}:
 1.0
 2.0

julia> unfixed_model = unfix(fixed_model, @varname(m[1]));

julia> unfixed_model()  # (×) `m[1]` はまだ固定されています
2-element Vector{Float64}:
 1.0
 2.0

julia> # (✓) これは機能します
       unfixed_model_2 = fix(unfixed_model, @varname(m[1]) => missing);

julia> m = unfixed_model_2(); (m[1] ≠ 1.0 && m[2] == 2.0)
true
```
