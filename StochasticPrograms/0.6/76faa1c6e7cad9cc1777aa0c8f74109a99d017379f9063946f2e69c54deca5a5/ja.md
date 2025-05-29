```
@recourse(model, expr, args..., kw_args...)
```

`expr`で説明されるリコース意思決定変数を`model`に追加します。最終ステージの[`@stage`](@ref)ブロック内の[`@decision`](@ref)を置き換え、そこでのみ使用できます。構文の詳細については`@variable`を参照してください。

## 例

```julia
@recourse(model, 0 <= y <= 1)
```

他にも[`@decision`](@ref)、[`@parameters`](@ref)、[`@uncertain`](@ref)、[`@stage`](@ref)を参照してください。
