```
check_allocs(func, types; ignore_throw=true)
```

与えられた関数と型をLLVM IRにコンパイルし、アロケーションをチェックします。

`AllocationSite`、`DynamicDispatch`、および`AllocatingRuntimeCall`のベクターを返します。

!!! warning
    Julia言語/コンパイラは、この結果がJuliaの呼び出し間で安定していることを保証しません。

    安全性/正確性のためにアロケーションフリーのコードに依存する場合、テストコードで`check_allocs`を検証するだけでは不十分であり、プロダクションでの対応する呼び出しがランタイムでアロケートしないことを期待することはできません。

    この場合、代わりに`@check_allocs`を使用する必要があります。


# 例

```jldoctest
julia> function foo(x::Int, y::Int)
           z = x + y
           return z
       end
foo (generic function with 1 method)

julia> allocs = check_allocs(foo, (Int, Int))
AllocCheck.AllocationSite[]
```
