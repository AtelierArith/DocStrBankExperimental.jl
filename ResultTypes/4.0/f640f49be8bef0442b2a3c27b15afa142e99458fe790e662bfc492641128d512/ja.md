```
@try x err
@try(x, err)
```

もし `x` がエラーであれば、新しい例外 `err` を返します。そうでなければ、`x` をアンラップします。

このバージョンの @try は、例外を変換する必要はありません。

# 拡張ヘルプ

例:

```julia
function isbar(y)::Result{Bool, BarError}
    bad_value(y) && return BarError("不正な値: $y")
    return y == "bar"
end

function foo(x)::Result{Int, FooError}
    is_b = @try(isbar(x), FooError())
    return is_b ? 42 : 13
end
```
