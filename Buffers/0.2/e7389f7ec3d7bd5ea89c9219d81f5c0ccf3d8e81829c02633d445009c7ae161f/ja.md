```
@print_buffer_usage(buf, ex)
```

式 `ex` におけるバッファ `buf` の使用状況を出力します。

このマクロは、式 `ex` におけるバッファ `buf` の長さを計算する関数の本体を生成します。複数のバッファを使用する場合、例えば `@print_buffer_usage buf1 buf2 begin ... end` のようにマクロを使用することが可能です。

`buf` を引数とするすべての関数呼び出しは、`pseudo_<function>` 呼び出しに置き換えられます。`pseudo_alloc!`、`pseudo_drop!`、および `pseudo_reset!` 関数は事前に定義されており、必要に応じてカスタムの `pseudo_` 関数を定義することができます。

# 例

```julia
buf = Buffer(100000)
@print*buffer*usage buf begin
    if true
        A = alloc!(buf, 10, 10, 20)
    else
        A = alloc!(buf, 10, 10, 30)
    end
    B = alloc!(buf, 10, 10, 10)
    if true
        C = alloc!(buf, 10, 20)
    else
        C = alloc!(buf, 10, 30)
    end
    rand!(B)
    rand!(C)
    An = neuralyze(A)
    @tensor An[i,j,k] = B[i,j,l] * C[l,k]
    drop!(buf, B, C)
    reset!(buf)
end
```
