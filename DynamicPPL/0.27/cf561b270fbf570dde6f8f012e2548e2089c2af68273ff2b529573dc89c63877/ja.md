```
@submodel model
@submodel ... = model
```

Turingモデル内にネストされたTuring `model`を実行します。

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

モデル `demo2(missing, 0.4)` からサンプリングすると、ランダム変数 `x` がサンプリングされます：

```jldoctest submodel
julia> vi = VarInfo(demo2(missing, 0.4));

julia> @varname(x) in keys(vi)
true
```

変数 `a` は、`demo1` を実行したときに追跡されたランダム変数 `x` から計算できるため、追跡されません：

```jldoctest submodel
julia> @varname(a) in keys(vi)
false
```

`vi` に蓄積されたモデルの対数結合確率が正しいことを確認できます：

```jldoctest submodel
julia> x = vi[@varname(x)];

julia> getlogp(vi) ≈ logpdf(Normal(), x) + logpdf(Uniform(0, 1 + abs(x)), 0.4)
true
```
