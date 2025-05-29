```julia
struct SimpleVarInfo{NT, T, C<:DynamicPPL.AbstractTransformation} <: DynamicPPL.AbstractVarInfo
```

`logp`フィールドを持つパラメータのシンプルなラッパーで、対数密度の蓄積に使用されます。

現在、`NT<:NamedTuple`および`NT<:AbstractDict`にのみ実装されています。

# フィールド

  * `values`: 表現された実現の基礎となる表現
  * `logp`: 蓄積された対数確率を保持
  * `transformation`: 変数が変換されることを仮定するかどうかを表す

# 注意事項

これと`NTVarInfo`の主な違いは次のとおりです：

1. `SimpleVarInfo`は線形化を必要としません。
2. `SimpleVarInfo`はより効率的なバイジェクターを使用できます。
3. `SimpleVarInfo`は、`NT<:NamedTuple`の場合のみ型安定であり、a) チルダ文でインデックスを使用しないか、b) 値が正しい形状で指定されている必要があります。

# 例

## 一般的な使用法

```jldoctest simplevarinfo-general; setup=:(using Distributions)
julia> using StableRNGs

julia> @model function demo()
           m ~ Normal()
           x = Vector{Float64}(undef, 2)
           for i in eachindex(x)
               x[i] ~ Normal()
           end
           return x
       end
demo (generic function with 2 methods)

julia> m = demo();

julia> rng = StableRNG(42);

julia> ### サンプリング ###
       ctx = SamplingContext(rng, SampleFromPrior(), DefaultContext());

julia> # `NamedTuple`バージョンでは、"コンテナ"を使用している変数のために
       # プレースホルダー値を提供する必要があります。例えば、`Array`。
       # この場合、`m`ではなく`x`を指定する必要があります。
       _, vi = DynamicPPL.evaluate!!(m, SimpleVarInfo((x = ones(2), )), ctx);

julia> # (✓) ブンブン！速い!!!
       vi[@varname(x[1])]
0.4471218424633827

julia> # `x`を指す任意の変数名にもアクセスできます。例えば、
       vi[@varname(x)]
2-element Vector{Float64}:
 0.4471218424633827
 1.3736306979834252

julia> vi[@varname(x[1:2])]
2-element Vector{Float64}:
 0.4471218424633827
 1.3736306979834252

julia> # (×) コンテナを提供しない場合...
       _, vi = DynamicPPL.evaluate!!(m, SimpleVarInfo(), ctx); vi
ERROR: type NamedTuple has no field x
[...]

julia> # 変数名がわからない場合は、`OrderedDict`を代わりに使用できます。
       _, vi = DynamicPPL.evaluate!!(m, SimpleVarInfo{Float64}(OrderedDict()), ctx);

julia> # (✓) 速いですが、実行時にのみ可能です。
       vi[@varname(x[1])]
-1.019202452456547

julia> # さらに、モデルに表示される変数名としてのみアクセスできます！
       vi[@varname(x)]
ERROR: KeyError: key x not found
[...]

julia> vi[@varname(x[1:2])]
ERROR: KeyError: key x[1:2] not found
[...]
```

*技術的には*、`OrderedDict`の代わりに`AbstractDict`の任意の実装を使用することが可能ですが、`OrderedDict`は、例えば、varinfo内の値の線形化/フラット化などの特定の操作が評価間で一貫していることを保証します。したがって、ここで使用する`AbstractDict`の推奨実装は`OrderedDict`です。

*変換された*空間でもサンプリングできます：

```jldoctest simplevarinfo-general
julia> @model demo_constrained() = x ~ Exponential()
demo_constrained (generic function with 2 methods)

julia> m = demo_constrained();

julia> _, vi = DynamicPPL.evaluate!!(m, SimpleVarInfo(), ctx);

julia> vi[@varname(x)] # (✓) 0 ≤ x < ∞
1.8632965762164932

julia> _, vi = DynamicPPL.evaluate!!(m, DynamicPPL.settrans!!(SimpleVarInfo(), true), ctx);

julia> vi[@varname(x)] # (✓) -∞ < x < ∞
-0.21080155351918753

julia> xs = [last(DynamicPPL.evaluate!!(m, DynamicPPL.settrans!!(SimpleVarInfo(), true), ctx))[@varname(x)] for i = 1:10];

julia> any(xs .< 0)  # (✓) 負の数に対する正の確率質量！
true

julia> # もちろん`OrderedDict`でも！
       _, vi = DynamicPPL.evaluate!!(m, DynamicPPL.settrans!!(SimpleVarInfo(OrderedDict()), true), ctx);

julia> vi[@varname(x)] # (✓) -∞ < x < ∞
0.6225185067787314

julia> xs = [last(DynamicPPL.evaluate!!(m, DynamicPPL.settrans!!(SimpleVarInfo(), true), ctx))[@varname(x)] for i = 1:10];

julia> any(xs .< 0) # (✓) 負の数に対する正の確率質量！
true
```

もちろん、変換された空間での評価も機能します：

```jldoctest simplevarinfo-general
julia> vi = DynamicPPL.settrans!!(SimpleVarInfo((x = -1.0,)), true)
Transformed SimpleVarInfo((x = -1.0,), 0.0)

julia> # (✓) 負の数に対する正の確率質量！
       getlogp(last(DynamicPPL.evaluate!!(m, vi, DynamicPPL.DefaultContext())))
-1.3678794411714423

julia> # 変換されていることを示すのを忘れた場合：
       vi = DynamicPPL.settrans!!(SimpleVarInfo((x = -1.0,)), false)
SimpleVarInfo((x = -1.0,), 0.0)

julia> # (✓) 負の数に対する確率質量はありません！
       getlogp(last(DynamicPPL.evaluate!!(m, vi, DynamicPPL.DefaultContext())))
-Inf
```

## インデクシング

基礎ストレージとして`NamedTuple`を使用。

```jldoctest
julia> svi_nt = SimpleVarInfo((m = (a = [1.0], ), ));

julia> svi_nt[@varname(m)]
(a = [1.0],)

julia> svi_nt[@varname(m.a)]
1-element Vector{Float64}:
 1.0

julia> svi_nt[@varname(m.a[1])]
1.0

julia> svi_nt[@varname(m.a[2])]
ERROR: BoundsError: attempt to access 1-element Vector{Float64} at index [2]
[...]

julia> svi_nt[@varname(m.b)]
ERROR: type NamedTuple has no field b
[...]
```

基礎ストレージとして`OrderedDict`を使用。

```jldoctest
julia> svi_dict = SimpleVarInfo(OrderedDict(@varname(m) => (a = [1.0], )));

julia> svi_dict[@varname(m)]
(a = [1.0],)

julia> svi_dict[@varname(m.a)]
1-element Vector{Float64}:
 1.0

julia> svi_dict[@varname(m.a[1])]
1.0

julia> svi_dict[@varname(m.a[2])]
ERROR: BoundsError: attempt to access 1-element Vector{Float64} at index [2]
[...]

julia> svi_dict[@varname(m.b)]
ERROR: type NamedTuple has no field b
[...]
```
