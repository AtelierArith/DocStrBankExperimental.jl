```
onehot(x, labels, [default])
```

[`OneHotVector`](@ref)を返します。これはおおよそ`x .== labels`のスパース表現です。

例えば`Vector{Bool}`を保存する代わりに、`labels`内の`x`の最初の出現のインデックスを保存します。もし`x`がlabels内に見つからない場合、`onehot(default, labels)`を返すか、デフォルトが指定されていない場合はエラーを返します。

多くの`x`にこれを適用するには[`onehotbatch`](@ref)を、これらのいずれかを逆にするには[`onecold`](@ref)を、また`argmax`を一般化するために使用します。

# 例

```jldoctest
julia> β = onehot(:b, (:a, :b, :c))
3-element OneHotVector(::UInt32) with eltype Bool:
 ⋅
 1
 ⋅

julia> αβγ = (onehot(0, 0:2), β, onehot(:z, [:a, :b, :c], :c))  # デフォルトを使用
(Bool[1, 0, 0], Bool[0, 1, 0], Bool[0, 0, 1])

julia> hcat(αβγ...)  # スパース性を保持
3×3 OneHotMatrix(::Vector{UInt32}) with eltype Bool:
 1  ⋅  ⋅
 ⋅  1  ⋅
 ⋅  ⋅  1
```
