```
reshape_buf!(buf, dims...; offset=0, extend=true)
```

バッファの一部を指定された次元に再形成します（コピーせずに）、`offset`を使用して。

`ThreadsBuffer`の場合、現在のスレッドのバッファを再形成します。使用後は[`reset!(::ThreadsBuffer)`](@ref)または[`release!`](@ref)を呼び出してください。

これは、テンソル収縮の中間結果などに使用できます。

!!! warning
    同じバッファに対して[`alloc!`](@ref)または[`drop!`](@ref)と一緒にこの関数を使用しないでください！


# 例

```julia
julia> buf = Buffer(100000)
julia> A = reshape_buf!(buf, 10, 10, 20) # 10x10x20 テンソル
julia> B = reshape_buf!(buf, 10, 10, 10, offset=2000) # 2001から始まる10x10x10 テンソル
julia> B .= rand(10,10,10)
julia> C = rand(10,20)
julia> @tensor A[i,j,k] = B[i,j,l] * C[l,k]
```
