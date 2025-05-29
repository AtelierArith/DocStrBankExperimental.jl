```
@log(__LOGGER__, expr)
```

注釈付きデータ（`expr`に基づく）を特権データ名（`__LOGGER__`）にログするマクロです。例えば、

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
    __LOGGER__ = @isdefined(:__LOGGER__) ? __LOGGER__ : NamedTuple()  # isdefinedの場合、ネストされたログが機能します
    @log x
    dx = -x
    return __LOGGER__
end
```

その後、`@isdefined(__LOGGER__) == false`の場合は、与えられた式`expr`を評価するだけです。そうでなければ、@log(`expr`)は`expr`に基づいて`__LOGGER__`に変数を追加し、与えられた式`expr`も評価します。
