```
@add_predicate qc desc pred
```

述語 `pred` を説明 `desc` とともにテストのセット `qc` に追加します。

# 引数

  * `qc`: [`Quickcheck`](@ref Quickcheck) 型のオブジェクト
  * `desc`: 述語を説明する文字列
  * `pred`: [無名関数](https://docs.julialang.org/en/v1/manual/functions/#man-anonymous-functions) の形をした述語

# 注意事項

`pred` の形は非常に厳格です：

  * 無名関数でなければなりません。形式的には、`->` 型の `Expr` である必要があります。
  * `pred` の左側に現れる各引数の型は `x::Type` 構文で指定する必要があります。
  * `pred` の引数の名前は重要です！具体的には、特定の [`Quickcheck`](@ref Quickcheck) オブジェクト内では、すべての引数の型が述語間で一貫している必要があります（例を参照）。
  * 特定の [`Quickcheck`](@ref Quickcheck) オブジェクトに保存される各述語には、異なる説明が与えられなければなりません。

# 例

```jldoctest
julia> qc = Quickcheck("A Test")
A Test: 0 predicate and 0 free variable.

julia> @add_predicate qc "Identity" (x::Float64 -> x == x)
A Test: 1 predicate and 1 free variable.
x::Float64

julia> @add_predicate qc "Sum commute" ((n::Int, x::Float64) -> n + x == x + n)
A Test: 2 predicates and 2 free variables:
n::Int64
x::Float64

julia> @add_predicate qc "Is odd" isodd(x)
ERROR: Predicate declaration must have the form of an anonymous function (... -> ...)
[...]

julia> @add_predicate qc "Is odd" (x::Int -> is_odd(x))
ERROR: A declaration for variable x already exists with type Float64; please choose another name for x
[...]
```
