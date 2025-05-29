```
@submodel prefix=... model
@submodel prefix=... ... = model
```

Turingの`model`をTuringモデルの内部でネストして実行し、`model`内のすべてのランダム変数に"`prefix`."をプレフィックスとして追加します。

`prefix=...`の有効な表現は次のとおりです：

  * `prefix=false`: プレフィックスは使用されません。
  * `prefix=true`: 左辺の`... = model`からプレフィックスを自動的に決定しようとします。最初に`VarName`に変換し、その後`Symbol`を呼び出します。
  * `prefix=expression`: プレフィックスは`Symbol(expression)`になります。

プレフィックスを使用することで、同じTuringモデルを複数回実行しながら、すべてのランダム変数を正しく追跡することが可能になります。

!!! warning
    これは非推奨であり、将来のリリースで削除されます。代わりに`left ~ to_submodel(model)`を使用してください（[`to_submodel(model)`](@ref)を参照）。


# 例

## 例のモデル

```jldoctest submodelprefix; setup=:(using Distributions)
julia> @model function demo1(x)
           x ~ Normal()
           return 1 + abs(x)
       end;

julia> @model function demo2(x, y, z)
            @submodel prefix="sub1" a = demo1(x)
            @submodel prefix="sub2" b = demo1(y)
            return z ~ Uniform(-a, b)
       end;
```

モデル`demo2(missing, missing, 0.4)`からサンプリングすると、ランダム変数`sub1.x`と`sub2.x`がサンプリングされます：

```jldoctest submodelprefix
julia> vi = VarInfo(demo2(missing, missing, 0.4));
┌ Warning: `@submodel model`と`@submodel prefix=... model`は非推奨です; 最新の構文については`to_submodel`を参照してください。
│   caller = ip:0x0
└ @ Core :-1

julia> @varname(sub1.x) in keys(vi)
true

julia> @varname(sub2.x) in keys(vi)
true
```

変数`a`と`b`は、`demo1`を実行したときに追跡されたランダム変数`sub1.x`と`sub2.x`から計算できるため、追跡されません：

```jldoctest submodelprefix
julia> @varname(a) in keys(vi)
false

julia> @varname(b) in keys(vi)
false
```

`vi`に蓄積されたモデルの対数結合確率が正しいことを確認できます：

```jldoctest submodelprefix
julia> sub1_x = vi[@varname(sub1.x)];

julia> sub2_x = vi[@varname(sub2.x)];

julia> logprior = logpdf(Normal(), sub1_x) + logpdf(Normal(), sub2_x);

julia> loglikelihood = logpdf(Uniform(-1 - abs(sub1_x), 1 + abs(sub2_x)), 0.4);

julia> getlogp(vi) ≈ logprior + loglikelihood
true
```

## プレフィックスの設定方法の違い

```jldoctest submodel-prefix-alternatives; setup=:(using DynamicPPL, Distributions)
julia> @model inner() = x ~ Normal()
inner (generic function with 2 methods)

julia> # `prefix`が指定されていない場合、プレフィックスは使用されません。
       @model submodel_noprefix() = @submodel a = inner()
submodel_noprefix (generic function with 2 methods)

julia> @varname(x) in keys(VarInfo(submodel_noprefix()))
┌ Warning: `@submodel model`と`@submodel prefix=... model`は非推奨です; 最新の構文については`to_submodel`を参照してください。
│   caller = ip:0x0
└ @ Core :-1
true

julia> # 明示的にプレフィックスを使用しない。
       @model submodel_prefix_false() = @submodel prefix=false a = inner()
submodel_prefix_false (generic function with 2 methods)

julia> @varname(x) in keys(VarInfo(submodel_prefix_false()))
┌ Warning: `@submodel model`と`@submodel prefix=... model`は非推奨です; 最新の構文については`to_submodel`を参照してください。
│   caller = ip:0x0
└ @ Core :-1
true

julia> # `a`から自動的に決定されます。
       @model submodel_prefix_true() = @submodel prefix=true a = inner()
submodel_prefix_true (generic function with 2 methods)

julia> @varname(a.x) in keys(VarInfo(submodel_prefix_true()))
┌ Warning: `@submodel model`と`@submodel prefix=... model`は非推奨です; 最新の構文については`to_submodel`を参照してください。
│   caller = ip:0x0
└ @ Core :-1
true

julia> # 静的文字列を使用。
       @model submodel_prefix_string() = @submodel prefix="my prefix" a = inner()
submodel_prefix_string (generic function with 2 methods)

julia> @varname(var"my prefix".x) in keys(VarInfo(submodel_prefix_string()))
┌ Warning: `@submodel model`と`@submodel prefix=... model`は非推奨です; 最新の構文については`to_submodel`を参照してください。
│   caller = ip:0x0
└ @ Core :-1
true

julia> # 文字列補間を使用。
       @model submodel_prefix_interpolation() = @submodel prefix="$(nameof(inner()))" a = inner()
submodel_prefix_interpolation (generic function with 2 methods)

julia> @varname(inner.x) in keys(VarInfo(submodel_prefix_interpolation()))
┌ Warning: `@submodel model`と`@submodel prefix=... model`は非推奨です; 最新の構文については`to_submodel`を参照してください。
│   caller = ip:0x0
└ @ Core :-1
true

julia> # または任意の式を使用。
       @model submodel_prefix_expr() = @submodel prefix=1 + 2 a = inner()
submodel_prefix_expr (generic function with 2 methods)

julia> @varname(var"3".x) in keys(VarInfo(submodel_prefix_expr()))
┌ Warning: `@submodel model`と`@submodel prefix=... model`は非推奨です; 最新の構文については`to_submodel`を参照してください。
│   caller = ip:0x0
└ @ Core :-1
true

julia> # (×) 左辺の式がない場合の自動プレフィックスは機能しません！
       @model submodel_prefix_error() = @submodel prefix=true inner()
ERROR: LoadError: 左辺がないのに自動的にプレフィックスを付けることはできません
[...]
```

# 注意

  * `prefix=expression`を選択すると、プレフィックス付けには実行時コストがかかります。これは、右辺の`... = model`の式が実行時情報を必要とするかどうかに依存して、`prefix=true`の場合も同様です。例えば、`x = model`は*静的*プレフィックス`x`を生成しますが、`x[i] = model`は実行時に解決されます。
