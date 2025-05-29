```
@Loggable(defun)
```

関数定義から2つのメソッドを生成します（`defun`）。

# 注意事項

マクロ`@Loggable`を使用した関数定義は、同じ名前の2つのメソッド（汎用関数）を生成します。例えば、

```julia
@Loggable function dynamics!(dx, x, p, t; kwargs...)
    @log x
    dx = -x
end
```

は次のように生成されます。

```julia
function dynamics!(dx, x, p, t; kwargs...)
    @log x
    dx = -x
end
function dynamics!(dx, x, p, t, __log_indicator__::__LOG_INDICATOR__; kwargs...)
    __LOGGER__ = @isdefined(:__LOGGER__) ? __LOGGER__ : NamedTuple()  # isdefinedの場合、ネストされたロギングが機能します
    @log x
    dx = -x
    return __LOGGER__
end
```
