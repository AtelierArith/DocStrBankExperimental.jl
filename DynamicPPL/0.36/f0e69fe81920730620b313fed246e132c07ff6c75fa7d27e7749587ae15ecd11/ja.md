```
to_submodel(model::Model[, auto_prefix::Bool])
```

サンプル可能なモデルであることを示すモデルラッパーを返します。

これは主に、モデルがサンプリング可能であるが、その対数密度を評価する必要はないことを示すために、`~` 演算子の右側で使用されることを意図しています。

!!! warning
    `left ~ right` の形の式に通常関連付けられる他の操作（[`condition`](@ref) など）も `to_submodel` では機能しないことに注意してください。


!!! warning
    モデル間で変数名が衝突するのを避けるために、引数 `auto_prefix` を `true` に設定しておくことをお勧めします。自動プレフィックスを使用しない場合は、明示的に [`prefix(::Model, input)`](@ref) を使用することをお勧めします。


# 引数

  * `model::Model`: ラップするモデル。
  * `auto_prefix::Bool`: `~` ステートメントの左側を使用してモデル内の変数を自動的にプレフィックスするかどうか。デフォルト: `true`。

# 例

## 簡単な例

```jldoctest submodel-to_submodel; setup=:(using Distributions)
julia> @model function demo1(x)
           x ~ Normal()
           return 1 + abs(x)
       end;

julia> @model function demo2(x, y)
            a ~ to_submodel(demo1(x))
            return y ~ Uniform(0, a)
       end;
```

モデル `demo2(missing, 0.4)` からサンプリングすると、ランダム変数 `x` がサンプリングされます：

```jldoctest submodel-to_submodel
julia> vi = VarInfo(demo2(missing, 0.4));

julia> @varname(a.x) in keys(vi)
true
```

変数 `a` は追跡されません。しかし、`demo1` の戻り値が割り当てられ、モデルの後続の行で使用できるようになります。

```jldoctest submodel-to_submodel
julia> @varname(a) in keys(vi)
false
```

`vi` に蓄積されたモデルの対数結合確率が正しいことを確認できます：

```jldoctest submodel-to_submodel
julia> x = vi[@varname(a.x)];

julia> getlogp(vi) ≈ logpdf(Normal(), x) + logpdf(Uniform(0, 1 + abs(x)), 0.4)
true
```

## 自動プレフィックスなし

前述のように、デフォルトでは、`auto_prefix` 引数はサブモデル内の変数を自動的にプレフィックスするかどうかを指定します。`auto_prefix=false` の場合、サブモデル内の変数はプレフィックスされません。

```jldoctest submodel-to_submodel-prefix; setup=:(using Distributions)
julia> @model function demo1(x)
           x ~ Normal()
           return 1 + abs(x)
       end;

julia> @model function demo2_no_prefix(x, z)
            a ~ to_submodel(demo1(x), false)
            return z ~ Uniform(-a, 1)
       end;

julia> vi = VarInfo(demo2_no_prefix(missing, 0.4));

julia> @varname(x) in keys(vi)  # ここでは `a.x` の代わりに `x` を使用しています
true
```

しかし、プレフィックスを使用しないことは一般的には推奨されません。注意しないと変数名の衝突を引き起こす可能性があります。たとえば、同じモデルをモデル内で2回再利用する場合、プレフィックスを使用しないと変数名の衝突が発生します。しかし、[`prefix(::Model, input)`](@ref) を使用して手動でプレフィックスを付けることができます：

```jldoctest submodel-to_submodel-prefix
julia> @model function demo2(x, y, z)
            a ~ to_submodel(prefix(demo1(x), :sub1), false)
            b ~ to_submodel(prefix(demo1(y), :sub2), false)
            return z ~ Uniform(-a, b)
       end;

julia> vi = VarInfo(demo2(missing, missing, 0.4));

julia> @varname(sub1.x) in keys(vi)
true

julia> @varname(sub2.x) in keys(vi)
true
```

変数 `a` と `b` は追跡されませんが、それぞれの `demo1` の呼び出しの戻り値が割り当てられます：

```jldoctest submodel-to_submodel-prefix
julia> @varname(a) in keys(vi)
false

julia> @varname(b) in keys(vi)
false
```

`vi` に蓄積されたモデルの対数結合確率が正しいことを確認できます：

```jldoctest submodel-to_submodel-prefix
julia> sub1_x = vi[@varname(sub1.x)];

julia> sub2_x = vi[@varname(sub2.x)];

julia> logprior = logpdf(Normal(), sub1_x) + logpdf(Normal(), sub2_x);

julia> loglikelihood = logpdf(Uniform(-1 - abs(sub1_x), 1 + abs(sub2_x)), 0.4);

julia> getlogp(vi) ≈ logprior + loglikelihood
true
```

## 尤度としての使用は違法

`to_submodel` モデルを他のモデルの尤度として使用することは違法であることに注意してください：

```jldoctest submodel-to_submodel-illegal; setup=:(using Distributions)
julia> @model inner() = x ~ Normal()
inner (generic function with 2 methods)

julia> @model illegal_likelihood() = a ~ to_submodel(inner())
illegal_likelihood (generic function with 2 methods)

julia> model = illegal_likelihood() | (a = 1.0,);

julia> model()
ERROR: ArgumentError: `~` with a model on the right-hand side of an observe statement is not supported
[...]
```
