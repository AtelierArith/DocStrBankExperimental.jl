```
@check_allocs ignore_throw=true (function def)
```

提供された関数定義をラップし、その呼び出しがすべて自動的にアロケーションをチェックされるようにします。

チェックが失敗した場合、詳細な失敗を含む `AllocCheckFailure` 例外がスローされ、各欠陥のバックトレースが含まれます。

注意: ラップされた関数へのすべての呼び出しは実質的に動的ディスパッチであり、これは型が不安定であり、関数 *エントリ* でメモリをアロケートする可能性があることを意味します。 `@check_allocs` は、関数が実行を開始した後にアロケーションがないことを保証するだけです。

# 例

```jldoctest
julia> @check_allocs multiply(x,y) = x*y
multiply (generic function with 1 method)

julia> multiply(1.5, 3.5) # Float64 の場合、アロケーションはなし
5.25

julia> multiply(rand(3,3), rand(3,3)) # 行列の積は結果をアロケートする必要がある
ERROR: @check_allocs 関数は 1 回のアロケーションを含んでいます。

Stacktrace:
 [1] macro expansion
   @ ~/repos/AllocCheck/src/macro.jl:134 [inlined]
 [2] multiply(x::Matrix{Float64}, y::Matrix{Float64})
   @ Main ./REPL[2]:133
 [3] top-level scope
   @ REPL[5]:1
```
