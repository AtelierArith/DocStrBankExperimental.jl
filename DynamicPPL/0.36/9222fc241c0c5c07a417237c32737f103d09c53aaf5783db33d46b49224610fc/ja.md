```
values_as_in_model(model::Model, include_colon_eq::Bool, varinfo::AbstractVarInfo[, context::AbstractContext])
```

モデルで見られるように`varinfo`の値を取得します。

より具体的には、このメソッドは*モデルで見られるように*実現を抽出しようとします。例えば、`x[1] ~ truncated(Normal(); lower=0)`は、`truncated(Normal(); lower=0)`と互換性のある実現をもたらします。つまり、`x[1]`の値が正であるような実現です。これは、`varinfo`が制約のない空間で動作しているかどうかに関係ありません。

したがって、このメソッドは追加のモデル評価のコストをかけて、制約のある空間での実現を取得する「安全な」方法です。

# 引数

  * `model::Model`: 実現を抽出するモデル。
  * `include_colon_eq::Bool`: `:=`の左辺にある変数も含めるかどうか。
  * `varinfo::AbstractVarInfo`: 抽出に使用する変数情報。
  * `context::AbstractContext`: 抽出に使用する基本コンテキスト。デフォルトは`DynamicPPL.DefaultContext()`です。

# 例

## `VarInfo`が失敗する場合

以下は、[`VarInfo`](@ref)と制約のある変数を扱う際の一般的な落とし穴を示しています。

```jldoctest
julia> using Distributions, StableRNGs

julia> rng = StableRNG(42);

julia> @model function model_changing_support()
           x ~ Bernoulli(0.5)
           y ~ x == 1 ? Uniform(0, 1) : Uniform(11, 12)
       end;

julia> model = model_changing_support();

julia> # 初期の型安定な`VarInfo`を構築します。
       varinfo = VarInfo(rng, model);

julia> # 制約のない空間で動作するようにリンクします。
       varinfo_linked = DynamicPPL.link(varinfo, model);

julia> # 制約のない空間で計算を行います。例えば、`θ`の値を変更します。
       # `x`を反転させて`y`の他のサポートに到達します。
       θ = [!varinfo[@varname(x)], rand(rng)];

julia> # 新しい値で`VarInfo`を更新します。
       varinfo_linked = DynamicPPL.unflatten(varinfo_linked, θ);

julia> # `y`の期待されるサポートを決定します。
       lb, ub = θ[1] == 1 ? (0, 1) : (11, 12)
(0, 1)

julia> # アプローチ1: `invlink`を使用して制約のある空間に戻し、抽出します。
       varinfo_invlinked = DynamicPPL.invlink(varinfo_linked, model);

julia> # (×) 失敗！`VarInfo`は最初のモデル評価で使用された元の分布を
       # _保存_するため、`x`が変更されても`y`のサポートは更新されません。
       lb ≤ first(varinfo_invlinked[@varname(y)]) ≤ ub
false

julia> # アプローチ2: `values_as_in_model`を使用して実現を抽出します。
       # (✓) `values_as_in_model`はモデルを再実行し、`x`の新しい値に基づいて
       # `y`の正しい実現を抽出します。
       lb ≤ values_as_in_model(model, true, varinfo_linked)[@varname(y)] ≤ ub
true
```
