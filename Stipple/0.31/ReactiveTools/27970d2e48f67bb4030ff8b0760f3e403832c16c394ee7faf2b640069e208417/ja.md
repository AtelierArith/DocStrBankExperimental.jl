```julia
@onchange(var, expr)
```

反応的な更新を宣言し、反応的な変数が変化したときに `expr` が実行されます。

**使用法**

このマクロは変数のリストを監視し、変数が変化したときに実行されるコードブロックを定義します。

```julia
@app begin
    # UI から値を取得する反応的変数
    @in N = 0
    @in M = 0
    @out result = 0
    # N が変化したときに実行される反応的コード
    @onchange N, M begin
        result = 10*N*M
    end
end
```
