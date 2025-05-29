```
decondition(model::Model)
decondition(model::Model, variables...)
```

`variables...` が *観測* として考慮されない `Model` を返します。`variables` が提供されていない場合、現在観測として考慮されているすべての変数はもはや考慮されません。

これは本質的に [`condition`](@ref) の逆です。これは同様の制限を受けることも意味します。

現在、`variables` が `condition` に提供された明示的な値を取ることのみをサポートしていることに注意してください。

# 例

```jldoctest decondition
julia> using Distributions

julia> @model function demo()
           m ~ Normal()
           x ~ Normal(m, 1)
           return (; m=m, x=x)
       end
demo (generic function with 2 methods)

julia> conditioned_model = condition(demo(), m = 1.0, x = 10.0);

julia> conditioned_model()
(m = 1.0, x = 10.0)

julia> # `decondition` に `VarName` を指定することによって。
       model = decondition(conditioned_model, @varname(m));

julia> (m, x) = model(); (m ≠ 1.0 && x == 10.0)
true

julia> # `NamedTuple` が基盤として使用される場合、シンボルを直接提供することもできます
       # （ただし、変数がコンパイル時に知られている場合は `@varname` アプローチが好ましいです）。
       model = decondition(conditioned_model, :m);

julia> (m, x) = model(); (m ≠ 1.0 && x == 10.0)
true

julia> # 複数の `decondition` を一度に行う：
       (m, x) = decondition(model, :m, :x)(); (m ≠ 1.0 && x ≠ 10.0)
true

julia> # シンボルなしで `decondition` すると、すべての変数が `decondition` されます。
       (m, x) = decondition(model)(); (m ≠ 1.0 && x ≠ 10.0)
true

julia> # 可能であればコンパイル時に `decondition` を実行するための `Val` の使用もサポートされています。
       model = decondition(conditioned_model, Val{:m}());

julia> (m, x) = model(); (m ≠ 1.0 && x == 10.0)
true
```

同様に `Dict` を使用する場合：

```jldoctest decondition
julia> conditioned_model_dict = condition(demo(), @varname(m) => 1.0, @varname(x) => 10.0);

julia> conditioned_model_dict()
(m = 1.0, x = 10.0)

julia> deconditioned_model_dict = decondition(conditioned_model_dict, @varname(m));

julia> (m, x) = deconditioned_model_dict(); m ≠ 1.0 && x == 10.0
true
```

しかし、前述のように、`decondition` は以前に `condition` に明示的に提供された変数にのみサポートされています；

```jldoctest decondition
julia> @model function demo_mv(::Type{TV}=Float64) where {TV}
           m = Vector{TV}(undef, 2)
           m[1] ~ Normal()
           m[2] ~ Normal()
           return m
       end
demo_mv (generic function with 4 methods)

julia> model = demo_mv();

julia> conditioned_model = condition(model, @varname(m) => [1.0, 2.0]);

julia> conditioned_model()
2-element Vector{Float64}:
 1.0
 2.0

julia> deconditioned_model = decondition(conditioned_model, @varname(m[1]));

julia> deconditioned_model()  # (×) `m[1]` はまだ条件付けされています
2-element Vector{Float64}:
 1.0
 2.0

julia> # (✓) これは機能します
       deconditioned_model_2 = deconditioned_model | (@varname(m[1]) => missing);

julia> m = deconditioned_model_2(); (m[1] ≠ 1.0 && m[2] == 2.0)
true
```
