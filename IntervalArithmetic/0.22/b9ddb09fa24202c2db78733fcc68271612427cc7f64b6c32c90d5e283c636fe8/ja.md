```
ExactReal{T<:Real} <: Real
```

実数は、その二進数形式で記述された数値に正確に対応することが保証されています。目的は、非区間数が正確であることを保証することであり、`ExactReal`は`Interval`と共に使用される際に「NG」フラグを生成しないようにします。

!!! danger
    `ExactReal`を使用することにより、ユーザーは入力した数値が意図した値に対応していることを確認する責任を認めます。例えば、`ExactReal(0.1)`は、ユーザーが$0.1$が二進数として正確に表現できないことを知っており、$0.1$とはわずかに異なる数値を使用していることを意味します。二進数を特定するために、`ExactReal`は丸めなしで表示されます。

    ```julia
    julia> ExactReal(0.1)
    ExactReal{Float64}(0.1000000000000000055511151231257827021181583404541015625)
    ```

    疑問がある場合は、[`has_exact_display`](@ref)を使用して、`Real`の文字列表現がその二進数値と等しいかどうかを確認できます。


# 例

```jldoctest
julia> setdisplay(:full);

julia> 0.5 * interval(1)
Interval{Float64}(0.5, 0.5, com)_NG

julia> ExactReal(0.5) * interval(1)
Interval{Float64}(0.5, 0.5, com)

julia> [1, interval(2)]
2-element Vector{Interval{Float64}}:
 Interval{Float64}(1.0, 1.0, com)_NG
 Interval{Float64}(2.0, 2.0, com)

julia> [ExactReal(1), interval(2)]
2-element Vector{Interval{Float64}}:
 Interval{Float64}(1.0, 1.0, com)
 Interval{Float64}(2.0, 2.0, com)
```

関連情報: [`@exact`](@ref).
