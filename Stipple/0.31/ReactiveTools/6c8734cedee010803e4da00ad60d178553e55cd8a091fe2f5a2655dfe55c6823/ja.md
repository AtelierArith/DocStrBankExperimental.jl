```julia
@out(expr)
```

公開かつ読み取り専用のリアクティブ変数を宣言します。

**使用法**

```julia
@app begin
    @out N = 0
end
```
