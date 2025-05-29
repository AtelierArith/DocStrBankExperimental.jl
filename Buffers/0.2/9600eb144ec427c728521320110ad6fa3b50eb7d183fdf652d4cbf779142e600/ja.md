```
with_buffer(f::Function, buf::ThreadsBuffer)
```

バッファ `buf` で関数 `f` を実行します。

関数が実行された後、バッファは解放されます。

# 例

```julia
julia> buf = Buffer(10000)
julia> C = alloc!(buf, 10, 10, 20) # 単一スレッドでの10x10x20の宛先テンソル
julia> tbuf = ThreadsBuffer(1000)
julia> Threads.@threads for k = 1:20
          with_buffer(tbuf) do bu
            A = alloc!(bu, 10, 10) # 10x10 テンソル
            B = alloc!(bu, 10, 10) # 10x10 テンソル
            rand!(A)
            rand!(B)
            @tensor C[:,:,k][i,j] = A[i,l] * B[l,j]
          end
        end
```
