```
@pdf drawing-instructions [width] [height] [filename]
```

PDF図面を作成してプレビューします。オプションで幅と高さを指定できます（デフォルトは600×600です）。ファイルは、指定された場合は`filename`として現在の作業ディレクトリに保存され、指定されていない場合は`luxor-drawing(timestamp).pdf`として保存されます。

これらの「ショートカット」マクロは、便利さとタイピングの手間を省くために設計されています。マクロ`@pdf ⟦ body ⟧ width height`は次のように展開されます：

```julia
Drawing(width, height, :pdf)
origin()
background("white")
sethue("black")
⟦ body ⟧
finish()
preview()
```

描画構築の完全な制御を行うには、ショートカットマクロではなく、これらの関数を直接使用してください。

### 例

```julia
@pdf circle(O, 20, :fill)
```

```julia
@pdf circle(O, 20, :fill) 400
```

```julia
@pdf circle(O, 20, :fill) 400 1200
```

```julia
@pdf circle(O, 20, :fill) 400 1200 "/tmp/A0-version"
```

```julia
@pdf circle(O, 20, :fill) 400 1200 "/tmp/A0-version.pdf"
```

```julia
@pdf begin
    setline(10)
    sethue("purple")
    circle(O, 20, :fill)
end
```

```julia
@pdf begin
    setline(10)
    sethue("purple")
    circle(O, 20, :fill)
end 1200 1200
```
