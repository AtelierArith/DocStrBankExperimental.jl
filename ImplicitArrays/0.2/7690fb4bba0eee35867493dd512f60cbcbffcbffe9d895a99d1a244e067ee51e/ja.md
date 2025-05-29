```
GenericInteractionFunction{R, C, T} <: InteractionFunction{R, C, T}
```

関数 `R × C → T` は、与えられた関数の型安全なラッパーとして機能します。

# コンストラクタ

```
GenericInteractionFunction{R, C, T}(fun)
```

与えられた関数 `fun` からインタラクション関数を作成します。

# 例

```jldoctest; setup = :(using ImplicitArrays)
julia> f = GenericInteractionFunction{Int64, Int64, Int64}(+); f(9, 3)
12

julia> g = GenericInteractionFunction{Int64, Int64, Float64}(/); g(9, 3)
3.0

julia> h = GenericInteractionFunction{String, Int64, String}(repeat); h("abc", 3)
"abcabcabc"
```

!!! 注     インタラクション関数は、`fun(::R, ::C)` のメソッドが存在し、型 `T` の値を返す場合にのみ評価できます。そうでない場合、`MethodError` または `TypeError` がスローされます。
