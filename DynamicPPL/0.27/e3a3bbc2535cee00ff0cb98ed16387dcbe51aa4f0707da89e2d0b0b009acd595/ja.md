```
fix(model::Model; values...)
fix(model::Model, values::NamedTuple)
```

`values`の変数を固定として扱う`Model`を返します。

参照: [`unfix`](@ref), [`fixed`](@ref)

# 例

## 単純な単変量モデル

```jldoctest fix
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

julia> # `x`を観測値`100.0`として扱い、同様に`m=1.0`とする新しいインスタンスを作成します。
       fixed_model = fix(model, x=100.0, m=1.0);

julia> m, x = fixed_model(); (m == 1.0 && x == 100.0)
true

julia> # `x = 100.0`のみを固定しましょう。
       fixed_model = fix(model, x = 100.0);

julia> m, x = fixed_model(); (m ≠ 1.0 && x == 100.0)
true
```

上記は固定変数を保持するために`NamedTuple`を使用しており、これにより追加の最適化を行うことができます。多くの場合、上記はゼロの実行時オーバーヘッドです。

しかし、`Dict`を使用することもでき、これにより固定の柔軟性が向上します（以下の例を参照）が、一般的には`NamedTuple`アプローチよりもパフォーマンスが劣ります：

```jldoctest fix
julia> fixed_model_dict = fix(model, Dict(@varname(x) => 100.0));

julia> m, x = fixed_model_dict(); (m ≠ 1.0 && x == 100.0)
true

julia> # 別の方法: `Pair{<:VarName}`を位置引数として渡す。
       fixed_model_dict = fix(model, @varname(x) => 100.0, );

julia> m, x = fixed_model_dict(); (m ≠ 1.0 && x == 100.0)
true
```

## 多変量変数の一部のみを固定

多変量ランダム変数を固定するだけでなく、`fix`の呼び出しで何かを`missing`に設定する標準メカニズムを使用して、変数の一部のみを固定することもできます。

```jldoctest fix
julia> @model function demo_mv(::Type{TV}=Float64) where {TV}
           m = Vector{TV}(undef, 2)
           m[1] ~ Normal()
           m[2] ~ Normal()
           return m
       end
demo_mv (generic function with 4 methods)

julia> model = demo_mv();

julia> fixed_model = fix(model, m = [missing, 1.0]);

julia> # (✓) `m[1]`はサンプリングされ、`m[2]`は固定されています
       m = fixed_model(); (m[1] ≠ 1.0 && m[2] == 1.0)
true
```

直感的には、`fix(model, var"m[1]" = 1.0, )`のように書けることを期待するかもしれませんが、残念ながらこれはサポートされていません。これは、コンパイル時間を増加させる可能性があるためですが、実行時に関しては何の利益も提供しません：

```jldoctest fix
julia> # (×) `m[2]`は1.0に設定されていません。
       m = fix(model, var"m[2]" = 1.0)(); m[2] == 1.0
false
```

しかし、代わりに`Dict`を使用する場合はこれが可能です：

```jldoctest fix
julia> # 別の方法: `fix(model, Dict(@varname(m[2] => 1.0)))`
       # (✓) `m[2]`は1.0に設定されています。
       m = fix(model, @varname(m[2]) => 1.0)(); (m[1] ≠ 1.0 && m[2] == 1.0)
true
```

## ネストされたモデル

`fix`はもちろん、[`@submodel`](@ref)を使用してネストされたモデルの使用もサポートしています。

```jldoctest fix
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

julia> fixed_model = model | (m = 1.0, );

julia> fixed_model()
1.0
```

ただし、ネストされたモデル内の変数に接頭辞を付ける際には注意が必要です：

```jldoctest fix
julia> @model function demo_outer_prefix()
           @submodel prefix="inner" m = demo_inner()
           return m
       end
demo_outer_prefix (generic function with 2 methods)

julia> # (×) これは今は機能しません！
       fixed_model = demo_outer_prefix() | (m = 1.0, );

julia> fixed_model() == 1.0
false

julia> # (✓) `demo_inner`内の`m`は内部的に`inner.m`として参照されるため、次のようにします：
       fixed_model = demo_outer_prefix() | (var"inner.m" = 1.0, );

julia> fixed_model()
1.0

julia> # 上記の`var"..."`は標準のJulia構文であることに注意してください：
       keys((var"inner.m" = 1.0, ))
(Symbol("inner.m"),)
```

同様に`Dict`を使用する場合も：

```jldoctest fix
julia> fixed_model_dict = demo_outer_prefix() | (@varname(var"inner.m") => 1.0);

julia> fixed_model_dict()
1.0
```

これらの異なるモデルのトレース/`VarInfo`を見てみると、違いがより明確になるかもしれません：

```jldoctest fix
julia> keys(VarInfo(demo_outer()))
1-element Vector{VarName{:m, typeof(identity)}}:
 m

julia> keys(VarInfo(demo_outer_prefix()))
1-element Vector{VarName{Symbol("inner.m"), typeof(identity)}}:
 inner.m
```

これにより、異なるモデル内で`demo_inner`の`m`を固定する正しい方法がわかります。

## `condition`との違い

非常に似た機能が[`condition`](@ref)によって提供されており、驚くことではありませんが、*変数を条件付け*するのではなく固定します。固定と条件付けの唯一の違いは次のとおりです：

  * `condition`された変数は観測値と見なされ、したがって[`logjoint`](@ref)および[`loglikelihood`](@ref)の計算に含まれますが、[`logprior`](@ref)には含まれません。
  * `fix`された変数は定数と見なされ、したがっていかなる対数確率計算にも含まれません。

```juliadoctest fix
julia> @model function demo()
           m ~ Normal()
           x ~ Normal(m, 1)
           return (; m=m, x=x)
       end
demo (generic function with 2 methods)

julia> model = demo();

julia> model_fixed = fix(model, m = 1.0);

julia> model_conditioned = condition(model, m = 1.0);

julia> logjoint(model_fixed, (x=1.0,))
-0.9189385332046728

julia> # 異なる！
       logjoint(model_conditioned, (x=1.0,))
-2.3378770664093453

julia> # そしてその違いは`m`の欠落した対数確率です：
       logjoint(model_fixed, (x=1.0,)) + logpdf(Normal(), 1.0) == logjoint(model_conditioned, (x=1.0,))
true
```
