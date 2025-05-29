```
@draw drawing-instructions [width] [height]
```

PNG描画を作成してプレビューします。オプションで幅と高さを指定できます（デフォルトは600x600です）。描画はメモリに保存され、ディスク上のファイルには保存されません。

これらの「ショートカット」マクロは、便利さとタイピングの手間を省くために設計されています。マクロ `@draw ⟦ body ⟧ width height` は次のように展開されます：

```julia
Drawing(width, height, :png)
origin()
background("white")
sethue("black")
⟦ body ⟧
finish()
preview()
```

描画の構築を完全に制御するには、ショートカットマクロではなく、これらの関数を直接使用してください。

### 例

`@draw circle(O, 20, :fill)`

```julia
@draw circle(O, 20, :fill) 400
```

```julia
@draw circle(O, 20, :fill) 400 1200
```

```julia
@draw begin
    setline(10)
    sethue("purple")
    circle(O, 20, :fill)
end
```

```julia
@draw begin
    setline(10)
    sethue("purple")
    circle(O, 20, :fill)
end 1200 1200
```
