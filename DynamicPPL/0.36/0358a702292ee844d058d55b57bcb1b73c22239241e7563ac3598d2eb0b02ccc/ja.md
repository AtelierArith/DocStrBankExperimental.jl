```
@submodel model
@submodel ... = model
```

Turingモデルの中にネストされたTuring `model`を実行します。

!!! warning
    これは非推奨であり、将来のリリースで削除されます。代わりに`left ~ to_submodel(model)`を使用してください（[`to_submodel`](@ref)を参照）。


# 例

```jldoctest submodel; setup=:(using Distributions)
julia> @model function demo1(x)
           x ~ Normal()
           return 1 + abs(x)
       end;

julia> @model function demo2(x, y)
            @submodel a = demo1(x)
            return y ~ Uniform(0, a)
       end;
```

モデル`demo2(missing, 0.4)`からサンプリングすると、ランダム変数`x`がサンプリングされます：

```jldoctest submodel
julia> vi = VarInfo(demo2(missing, 0.4));
┌ Warning: `@submodel model`と`@submodel prefix=... model`は非推奨です; 最新の構文については`to_submodel`を参照してください。
│   caller = ip:0x0
└ @ Core :-1

julia> @varname(x) in keys(vi)
true
```

変数`a`は、`demo1`を実行したときに追跡されたランダム変数`x`から計算できるため、追跡されません：

```jldoctest submodel
julia> @varname(a) in keys(vi)
false
```

`vi`に蓄積されたモデルの対数結合確率が正しいことを確認できます：

```jldoctest submodel
julia> x = vi[@varname(x)];

julia> getlogp(vi) ≈ logpdf(Normal(), x) + logpdf(Uniform(0, 1 + abs(x)), 0.4)
true
```
