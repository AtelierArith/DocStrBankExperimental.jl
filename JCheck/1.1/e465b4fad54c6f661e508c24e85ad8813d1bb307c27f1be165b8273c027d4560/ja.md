```
specialcases(T)
```

非ランダムな入力は、常に[`@quickcheck`](@ref)によってチェックされます。

# 引数

  * `T::Type`: 入力の型

# 実装

  * あなたのメソッドは`Vector{T}`を返すべきです。
  * `T`のための[`generate`](@ref)メソッドがなければ無意味です。
  * 組み合わせ爆発に注意してください！[`@quickcheck`](@ref)は、偽にしようとしている述語のすべての引数の特別なケースの直積の各要素に対して入力を生成します。*本当に*特別なケースのみを含めてください。

# 例

```jldoctest
julia> specialcases(Int)
4-element Vector{Int64}:
                    0
                    1
 -9223372036854775808
  9223372036854775807

julia> specialcases(Float64)
4-element Vector{Float64}:
   0.0
   1.0
 -Inf
  Inf
```
