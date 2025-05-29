```
anova(::Type{FTest}, <model>; kwargs...)
anova(::Type{FTest}, <models>...; kwargs...)
```

F検定による分散分析。

`AnovaResult{M, FTest, N}`を返します。詳細については[`AnovaResult`](@ref)を参照してください。

  * `type`はanovaのタイプを指定します：

    1. 1つの`LinearModel`または`GeneralizedLinearModel`：1、2、3が有効です
    2. 1つの`LinearMixedModel`：1、3が有効です。
    3. その他：1のみが有効です。
  * `adjust_sigma`は、`LinearMixedModel`が最尤法でフィッティングされるときにREMLに調整するかどうかを決定します。

!!! note
    `adjust_sigma`を使用した結果は、REMLによって直接フィッティングされたモデルの結果からわずかに逸脱します。

