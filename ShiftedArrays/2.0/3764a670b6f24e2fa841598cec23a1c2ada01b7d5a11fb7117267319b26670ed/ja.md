```
CircShiftedArray(parent::AbstractArray, shifts)
```

カスタム `AbstractArray` オブジェクトで、`shifts` ステップだけ円環的にシフトされた `AbstractArray` `parent` を格納します（ここで `shifts` は `parent` の次元ごとに1つの `shift` 値を持つ `Tuple` です）。`copy` を使用して、`CircShiftedArray` の値を通常の `Array` に収集します。

!!! note
    `shift` は剰余演算で修正され、渡された値を保存せず、代わりに非負の数を保存します。これにより、同等のシフトが実現されます。


!!! note
    `parent` 自体が `CircShiftedArray` である場合、コンストラクタは `CircShiftedArray` オブジェクトをネストするのではなく、シフトを加算的に組み合わせます。


# 例

```jldoctest circshiftedarray
julia> v = [1, 3, 5, 4];

julia> s = CircShiftedArray(v, (1,))
4-element CircShiftedVector{Int64, Vector{Int64}}:
 4
 1
 3
 5

julia> copy(s)
4-element Vector{Int64}:
 4
 1
 3
 5
```
