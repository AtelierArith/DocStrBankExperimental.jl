```
smuggle(exception, stackframes=stacktrace(Base.catch_stacktrace()))
```

例外を密輸します。REPLでユーザーによって評価されたコードによってスローされた例外を報告するために使用できます。

!!! warning
    通知はすべての接続されたセッションに送信されます。


# 例

```julia
try
    error("foo")
catch exc
    smuggle(exc)
end
```
