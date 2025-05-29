```
@try x
@try(x)
```

もし `x` がエラーである場合（すなわち、`iserror(x) == true`）、エラーを解きほぐし、現在の関数から戻ります。そうでなければ、`x` を解きほぐします。

解きほぐされた例外が間違った型である場合、それを正しい型に変換する `Base.convert` メソッドが存在しなければなりません。（以下の拡張ヘルプの例を参照してください。）

このマクロは、`Result` を返す関数を呼び出す際のボイラープレートを削減することを目的としています。

# 拡張ヘルプ

`ResultTypes` を使用する典型的な関数のセットは、次のようになります。

```julia
Base.convert(::Type{FooError}, err::BarError) = FooError("Got a BarError: $(err.msg)")

function isbar(y)::Result{Bool, BarError}
    bad_value(y) && return BarError("Bad value: $y")
    return y == "bar"
end

function foo(x)::Result{Int, FooError}
    result = isbar(x)
    ResultTypes.iserror(result) && return unwrap_error(result)
    is_b = unwrap(result)

    return is_b ? 42 : 13
end
```

`@try` マクロを使用すると、`foo` は次のように短縮されます。

```julia
function foo(x)::Result{Int, FooError}
    is_b = @try(isbar(x))
    return is_b ? 42 : 13
end
```
