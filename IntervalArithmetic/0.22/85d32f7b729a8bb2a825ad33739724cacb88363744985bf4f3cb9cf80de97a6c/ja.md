```
@exact
```

式のすべてのリテラル数値を[`ExactReal`](@ref)でラップします。このマクロは、`Number`と[`Interval`](@ref)の引数の両方をシームレスに受け入れる汎用関数を定義することを可能にし、「NG」フラグを生成しません。

!!! danger
    [`ExactReal`](@ref)を使用することにより、ユーザーは入力した数値が意図した値に対応していることを確認する責任を認めます。たとえば、`ExactReal(0.1)`は、ユーザーが$0.1$が二進数として正確に表現できないことを知っており、$0.1$とはわずかに異なる数値を使用していることを意味します。二進数を特定するのを助けるために、`ExactReal`は丸めなしで表示されます。

    ```julia
    julia> ExactReal(0.1)
    ExactReal{Float64}(0.1000000000000000055511151231257827021181583404541015625)
    ```

    疑問がある場合は、[`has_exact_display`](@ref)を使用して、`Real`の文字列表現がその二進数値と等しいかどうかを確認できます。


# 例

```jldoctest
julia> setdisplay(:full);

julia> f(x) = 1.2*x + 0.1
f (generic function with 1 method)

julia> f(interval(1, 2))
Interval{Float64}(1.2999999999999998, 2.5, com)_NG

julia> @exact g(x) = 1.2*x + 0.1
g (generic function with 1 method)

julia> g(interval(1, 2))
Interval{Float64}(1.2999999999999998, 2.5, com)

julia> g(1.4)
1.78
```

参照: [`ExactReal`](@ref).
