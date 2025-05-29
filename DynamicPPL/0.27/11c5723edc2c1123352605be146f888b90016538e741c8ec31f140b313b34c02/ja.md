```
@submodel prefix=... model
@submodel prefix=... ... = model
```

Turingモデルの中にネストされたTuring `model`を実行し、`model`内のすべてのランダム変数に"`prefix`."をプレフィックスとして追加します。

`prefix=...`の有効な式は次のとおりです：

  * `prefix=false`: プレフィックスは使用されません。
  * `prefix=true`: 左辺の`... = model`からプレフィックスを自動的に決定しようとします。最初に`VarName`に変換し、その後`Symbol`を呼び出します。
  * `prefix=expression`: プレフィックスは`Symbol(expression)`になります。

プレフィックスを使用することで、同じTuringモデルを複数回実行しながら、すべてのランダム変数を正しく追跡することが可能になります。

# 例

## 例モデル

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

julia> @varname(var"sub1.x") in keys(vi)
true

julia> @varname(var"sub2.x") in keys(vi)
true
```

変数`a`と`b`は追跡されません。なぜなら、`demo1`を実行したときに追跡されたランダム変数`sub1.x`と`sub2.x`から計算できるからです：

```jldoctest submodelprefix
julia> @varname(a) in keys(vi)
false

julia> @varname(b) in keys(vi)
false
```

`vi`に蓄積されたモデルの対数結合確率が正しいことを確認できます：

```jldoctest submodelprefix
julia> sub1_x = vi[@varname(var"sub1.x")];

julia> sub2_x = vi[@varname(var"sub2.x")];

julia> logprior = logpdf(Normal(), sub1_x) + logpdf(Normal(), sub2_x);

julia> loglikelihood = logpdf(Uniform(-1 - abs(sub1_x), 1 + abs(sub2_x)), 0.4);

julia> getlogp(vi) ≈ logprior + loglikelihood
true
```

## プレフィックスを設定する異なる方法

```jldoctest submodel-prefix-alternatives; setup=:(using DynamicPPL, Distributions)
julia> @model inner() = x ~ Normal()
inner (generic function with 2 methods)

julia> # `prefix`が指定されていない場合、プレフィックスは使用されません。
       @model submodel_noprefix() = @submodel a = inner()
submodel_noprefix (generic function with 2 methods)

julia> @varname(x) in keys(VarInfo(submodel_noprefix()))
true

julia> # 明示的にプレフィックスを使用しない。
       @model submodel_prefix_false() = @submodel prefix=false a = inner()
submodel_prefix_false (generic function with 2 methods)

julia> @varname(x) in keys(VarInfo(submodel_prefix_false()))
true

julia> # `a`から自動的に決定される。
       @model submodel_prefix_true() = @submodel prefix=true a = inner()
submodel_prefix_true (generic function with 2 methods)

julia> @varname(var"a.x") in keys(VarInfo(submodel_prefix_true()))
true

julia> # 静的文字列を使用。
       @model submodel_prefix_string() = @submodel prefix="my prefix" a = inner()
submodel_prefix_string (generic function with 2 methods)

julia> @varname(var"my prefix.x") in keys(VarInfo(submodel_prefix_string()))
true

julia> # 文字列補間を使用。
       @model submodel_prefix_interpolation() = @submodel prefix="$(nameof(inner()))" a = inner()
submodel_prefix_interpolation (generic function with 2 methods)

julia> @varname(var"inner.x") in keys(VarInfo(submodel_prefix_interpolation()))
true

julia> # または任意の式を使用。
       @model submodel_prefix_expr() = @submodel prefix=1 + 2 a = inner()
submodel_prefix_expr (generic function with 2 methods)

julia> @varname(var"3.x") in keys(VarInfo(submodel_prefix_expr()))
true

julia> # (×) 左辺の式がない場合の自動プレフィックスは機能しません！
       @model submodel_prefix_error() = @submodel prefix=true inner()
ERROR: LoadError: cannot automatically prefix with no left-hand side
[...]
```

# 注意

  * `prefix=expression`を選択すると、プレフィックス付けにはランタイムコストがかかります。これは、`prefix=true`の場合も同様で、`... = model`の右辺の式がランタイム情報を必要とするかどうかによります。例えば、`x = model`は*静的*プレフィックス`x`を生成しますが、`x[i] = model`はランタイムで解決されます。
