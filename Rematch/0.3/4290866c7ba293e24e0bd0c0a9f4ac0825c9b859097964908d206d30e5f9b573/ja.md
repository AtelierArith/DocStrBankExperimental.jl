```
@match value begin
    pattern1 => result1
    pattern2 => result2
    ...
end
```

最初に一致する`pattern`の`result`を返します。一致がない場合は、`MatchFailure`をスローします。
