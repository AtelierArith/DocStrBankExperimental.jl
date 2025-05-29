```julia
@onbutton
```

UIでボタンが押されたときに`expr`を実行する反応的な更新を宣言します。

**使用法** `@click`でクリックイベントリスナーを定義し、`@onbutton`でハンドラーを定義します。

```julia
@app begin
    @in press = false
    @onbutton press begin
        println("ボタンが押されました！")
    end
end

ui() = btn("押してね", @click(:press))

@page("/", ui)
```
