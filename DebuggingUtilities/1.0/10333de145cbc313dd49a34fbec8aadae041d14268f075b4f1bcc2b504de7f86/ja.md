`@showln x` は "x = val" を出力します。ここで `val` は `x` の値であり、このステートメントが実行された関数、ファイル、および行番号に関する情報も含まれます。例えば：

```julia
function foo()
    x = 5
    @showln x
    x = 7
    @showln x
    nothing
end
```

は次のような出力を生成するかもしれません：

```
x = 5
(in foo at ./error.jl:26 at /tmp/showln_test.jl:52)
x = 7
(in foo at ./error.jl:26 at /tmp/showln_test.jl:54)
```

コールの深さに関する情報が必要な場合は、[`@showlnt`](@ref) を参照してください。
