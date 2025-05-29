```
condition(model::Model; values...)
condition(model::Model, values::NamedTuple)
```

`values`の変数を観測値として扱う`Model`を返します。

参照: [`decondition`](@ref), [`conditioned`](@ref)

# 制限事項

これは現在、モデルに引数として提供される変数では動作しません。たとえば、`@model function demo(x) ... end`は、`condition`が変数`x`に影響を与えないことを意味します。

したがって、`condition`と[`decondition`](@ref)を利用したい場合は、ランダム変数を引数として指定しないようにするべきです。

これは後方互換性のために行われています。

# 例

## 単純な一変量モデル

```jldoctest condition
julia> using Distributions

julia> @model function demo()
           m ~ Normal()
           x ~ Normal(m, 1)
           return (; m=m, x=x)
       end
demo (generic function with 2 methods)

julia> model = demo();

julia> m, x = model(); (m ≠ 1.0 && x ≠ 100.0)
true

julia> # `x`を観測値として`100.0`、同様に`m=1.0`として扱う新しいインスタンスを作成します。
       conditioned_model = condition(model, x=100.0, m=1.0);

julia> m, x = conditioned_model(); (m == 1.0 && x == 100.0)
true

julia> # `x = 100.0`のみに条件付けを行います。
       conditioned_model = condition(model, x = 100.0);

julia> m, x =conditioned_model(); (m ≠ 1.0 && x == 100.0)
true

julia> # より良い`|`構文を使用することもできます。
       conditioned_model = model | (x = 100.0, );

julia> m, x = conditioned_model(); (m ≠ 1.0 && x == 100.0)
true
```

上記は、条件付け変数を保持するために`NamedTuple`を使用しており、追加の最適化を行うことができます。多くの場合、上記はゼロの実行時オーバーヘッドです。

しかし、条件付けにおいてより柔軟性を提供する`Dict`を使用することもできます（以下の例を参照）。ただし、一般的に`NamedTuple`アプローチよりもパフォーマンスが劣ります。

```jldoctest condition
julia> conditioned_model_dict = condition(model, Dict(@varname(x) => 100.0));

julia> m, x = conditioned_model_dict(); (m ≠ 1.0 && x == 100.0)
true

julia> # 右辺を`Pair{<:VarName}`型の要素を持つタプルにすることで`|`を使用するオプションもあります。
       conditioned_model_dict = model | (@varname(x) => 100.0, );

julia> m, x = conditioned_model_dict(); (m ≠ 1.0 && x == 100.0)
true
```

## 多変量変数の一部のみを条件付ける

多変量ランダム変数に条件付けることができるだけでなく、`condition`の呼び出しで何かを`missing`に設定する標準メカニズムを使用して、変数の一部のみを条件付けることもできます。

```jldoctest condition
julia> @model function demo_mv(::Type{TV}=Float64) where {TV}
           m = Vector{TV}(undef, 2)
           m[1] ~ Normal()
           m[2] ~ Normal()
           return m
       end
demo_mv (generic function with 4 methods)

julia> model = demo_mv();

julia> conditioned_model = condition(model, m = [missing, 1.0]);

julia> # (✓) `m[1]`はサンプリングされ、`m[2]`は固定されています
       m = conditioned_model(); (m[1] ≠ 1.0 && m[2] == 1.0)
true
```

直感的には、`model | (m[1] = 1.0, )`と書けることを期待するかもしれませんが、これはコンパイル時間を増加させる可能性があるためサポートされていませんが、実行時に関しては何の利益もありません。

```jldoctest condition
julia> # (×) `m[2]`は1.0に設定されていません。
       m = condition(model, var"m[2]" = 1.0)(); m[2] == 1.0
false
```

しかし、基盤となるストレージとして`Dict`を使用する場合は、これを行うことができます。

```jldoctest condition
julia> # 代替案:
       # - `model | (@varname(m[2]) => 1.0,)`
       # - `condition(model, Dict(@varname(m[2] => 1.0)))`
       # (✓) `m[2]`は1.0に設定されています。
       m = condition(model, @varname(m[2]) => 1.0)(); (m[1] ≠ 1.0 && m[2] == 1.0)
true
```

## ネストされたモデル

`condition`はもちろん、[`@submodel`](@ref)を使用してネストされたモデルの使用もサポートしています。

```jldoctest condition
julia> @model demo_inner() = m ~ Normal()
demo_inner (generic function with 2 methods)

julia> @model function demo_outer()
           @submodel m = demo_inner()
           return m
       end
demo_outer (generic function with 2 methods)

julia> model = demo_outer();

julia> model() ≠ 1.0
true

julia> conditioned_model = model | (m = 1.0, );

julia> conditioned_model()
1.0
```

ただし、ネストされたモデル内の変数に接頭辞を付ける際には注意が必要です。

```jldoctest condition
julia> @model function demo_outer_prefix()
           @submodel prefix="inner" m = demo_inner()
           return m
       end
demo_outer_prefix (generic function with 2 methods)

julia> # (×) これは今は機能しません！
       conditioned_model = demo_outer_prefix() | (m = 1.0, );

julia> conditioned_model() == 1.0
false

julia> # (✓) `demo_inner`内の`m`は内部的に`inner.m`として参照されるため、次のようにします。
       conditioned_model = demo_outer_prefix() | (var"inner.m" = 1.0, );

julia> conditioned_model()
1.0

julia> # 上記の`var"..."`は標準的なJulia構文です。
       keys((var"inner.m" = 1.0, ))
(Symbol("inner.m"),)
```

同様に`Dict`を使用する場合も：

```jldoctest condition
julia> conditioned_model_dict = demo_outer_prefix() | (@varname(var"inner.m") => 1.0);

julia> conditioned_model_dict()
1.0
```

これらの異なるモデルのトレース/`VarInfo`を見てみると、違いがより明確になるかもしれません。

```jldoctest condition
julia> keys(VarInfo(demo_outer()))
1-element Vector{VarName{:m, typeof(identity)}}:
 m

julia> keys(VarInfo(demo_outer_prefix()))
1-element Vector{VarName{Symbol("inner.m"), typeof(identity)}}:
 inner.m
```

これにより、異なる2つのモデル内で`demo_inner`の`m`を条件付ける正しい方法がわかります。 ```
