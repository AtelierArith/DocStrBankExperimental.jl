```
broadcasted_normal(mu::AbstractArray{<:Real, N1},
                   std::AbstractArray{<:Real, N2}) where {N1, N2}
```

`Array{Float64, max(N1, N2)}`の形状`Broadcast.broadcast_shapes(size(mu), size(std))`のサンプルを生成します。各要素は独立に正規分布に従います。これは対角共分散行列を持つ多変量正規分布の（再形成された）形と同等ですが、このケースにおいてはより効率的な実装です。

`mu`と`std`の形状はブロードキャスト互換でなければなりません。

すべての引数が0次元配列である場合、`broadcasted_normal(...)`を介してサンプリングすると、`Array{Float64, 0}`を正しく返すのではなく、`Float64`を返します。これはこの件に関するJulia自身の不整合と一致しています：

```jldoctest
julia> typeof(ones())
Array{Float64,0}

julia> typeof(ones() .* ones())
Float64
```
