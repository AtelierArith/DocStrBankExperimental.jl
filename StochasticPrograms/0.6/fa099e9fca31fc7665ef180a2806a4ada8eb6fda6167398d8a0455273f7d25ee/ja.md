```
@decision(model, expr, args..., kw_args...)
```

`model`に`expr`で表される決定変数を追加します。[`@stage`](@ref)ブロック内で使用されると、作成された変数は後続のステージブロックで使用できます。最終ステージの決定をマークするには[`@recourse`](@ref)を使用する必要があります。構文の詳細については`@variable`を参照してください。

## 例

```julia
@decision(model, x >= 40)
```

他にも[`@recourse`](@ref)、[`@parameters`](@ref)、[`@uncertain`](@ref)、[`@stage`](@ref)を参照してください。
