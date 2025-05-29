```julia
@private(expr)
```

UIコードからアクセスできない非反応型変数を宣言します。

**使用法**

```julia
@app begin
    @private N = 0
end
```
