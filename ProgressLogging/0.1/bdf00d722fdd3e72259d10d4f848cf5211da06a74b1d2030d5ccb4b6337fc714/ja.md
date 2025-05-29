```
@withprogress [name=""] [parentid=uuid4()] ex
```

[`@logprogress`](@ref) を使用して、ログレベル、`_id`、および名前（ログメッセージ）を手動で指定することなく、進行状況ログイベントを発生させることができる字句環境を作成します。

```julia
@withprogress name="iterating" begin
    for i = 1:10
        sleep(0.5)
        @logprogress i/10
    end
end
```
