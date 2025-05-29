```
struct ConstInteractionFunction{R, C, T} <: InteractionFunction{R, C, T}
```

引数を無視して固定値を返すインタラクション関数 `R × C → T`。

# コンストラクタ

```
ConstInteractionFunction{R, C, T}(val)
```

常に `val` を返す定数インタラクション関数を作成します。

# 例

```jldoctest; setup = :(using ImplicitArrays)
julia> f = ConstInteractionFunction{Float64, Float64, Int64}(42);

julia> f(1.0, 1.5)
42
```
