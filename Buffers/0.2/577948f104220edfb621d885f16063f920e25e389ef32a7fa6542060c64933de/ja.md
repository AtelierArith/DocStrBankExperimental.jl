```
ThreadsBuffer{T}
```

スレッドごとに型 `T` のデータを格納するバッファオブジェクト。

デフォルトでは、バッファは `nthreads()` スレッド用に作成されます。つまり、各スレッドには独自のバッファ [`Buffer`](@ref) があります。

`ThreadsBuffer{T}(len, nbuf=Threads.nthreads())` を使用してバッファを作成し、[`alloc!`](@ref)、[`drop!`](@ref)、[`reset!`](@ref) などで使用します。

!!! warning
    使用後は必ず [`reset!`](@ref) または [`Buffers.release!`](@ref) を行ってバッファをリセットしてください！


!!! warning
    メモリは手動で割り当てられるため、バッファも手動で解放する必要があります。このバッファは、使用後にバッファを解放する [`@threadsbuffer`](@ref) マクロと一緒に使用することを意図しています。


# 例

```julia
julia> buf = Buffer(10000)
julia> C = alloc!(buf, 10, 10, 20) # 単一スレッドでの10x10x20の宛先テンソル
julia> @threadsbuffer tbuf(1000) begin # nthreads() スレッドごとの1000要素のバッファ
julia>  Threads.@threads for k = 1:20
          A = alloc!(tbuf, 10, 10) # 10x10 テンソル
          B = alloc!(tbuf, 10, 10) # 10x10 テンソル
          rand!(A)
          rand!(B)
          @tensor C[:,:,k][i,j] = A[i,l] * B[l,j]
          reset!(tbuf)
        end
       end
```
