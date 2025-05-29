```
add_click_info()
```

クリックイベントに関する情報をイベントオブジェクトに追加します。

### 例

```julia @app begin     @in x = 1 end

@methods add*click*info

@event :myclick begin     @info event     notify(**model**, "(x, y) clicked: (:(event["clientX"]), :(event["clientY"]))") end

ui() = cell("Hello world!", @on(:click, :myclick, :addClickInfo))
```
