```
ThreadsMAllocBuffer{T}
```

[`MAllocBuffer`](@ref) オブジェクトは、各スレッドのデータ型 `T` を格納するためのものです。

デフォルトでは、バッファは `nthreads()` スレッド用に作成されます。つまり、各スレッドには独自のバッファ [`MAllocBuffer`](@ref) があります。

`ThreadsMAllocBuffer{T}(len, nbuf=Threads.nthreads())` を使用してバッファを作成し、[`alloc!`](@ref)、[`drop!`](@ref)、[`reset!`](@ref) などで使用します。

!!! warning
    各スレッドで使用後は必ず [`reset!`](@ref) または [`Buffers.release!`](@ref) を行ってバッファをリセットしてください！


!!! warning
    メモリは手動で割り当てられるため、バッファも手動で解放する必要があります。このバッファは、使用後にバッファを解放する [`@threadsbuffer`](@ref) マクロと一緒に使用することを意図しています。


# 例

```julia
@buffer buf(10000) begin
  C = alloc!(buf, 10, 10, 20) # 単一スレッドでの 10x10x20 の宛先テンソル
  @threadsbuffer tbuf(1000) begin # nthreads() スレッドごとの 1000 要素のバッファ
    @sync for k = 1:20
      Threads.@spawn begin
        A = alloc!(tbuf, 10, 10) # 10x10 テンソル
        B = alloc!(tbuf, 10, 10) # 10x10 テンソル
        rand!(A)
        rand!(B)
        @tensor C[:,:,k][i,j] = A[i,l] * B[l,j]
        reset!(tbuf)
      end 
    end
  end # threadsbuffer tbuf を解放
end # バッファ buf を解放
```
