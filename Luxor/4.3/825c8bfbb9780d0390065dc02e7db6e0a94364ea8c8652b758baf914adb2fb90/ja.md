```
@eps drawing-instructions [width] [height] [filename]
```

EPS 描画を作成してプレビューします。オプションで幅と高さを指定できます（デフォルトは 600 x 600 です）。ファイルは、指定された場合は `filename` として現在の作業ディレクトリに保存され、指定されていない場合は `luxor-drawing(timestamp).eps` という名前になります。

一部のプラットフォームでは、EPS ファイルはプレビュー時に自動的に PDF に変換されます。

これらの「ショートカット」マクロは、便利さとタイピングの手間を省くために設計されています。マクロ `@draw ⟦ body ⟧ width height filename` は次のように展開されます：

```julia
Drawing(width, height, filename)
origin()
background("white")
sethue("black")
⟦ body ⟧
finish()
preview()
```

描画の構築を完全に制御するには、ショートカットマクロではなく、これらの関数を直接使用してください。

### 例

```julia
@eps circle(O, 20, :fill)
```

```julia
@eps circle(O, 20, :fill) 400
```

```julia
@eps circle(O, 20, :fill) 400 1200
```

```julia
@eps circle(O, 20, :fill) 400 1200 "/tmp/A0-version"
```

```julia
@eps circle(O, 20, :fill) 400 1200 "/tmp/A0-version.eps"
```

```julia
@eps begin
    setline(10)
    sethue("purple")
    circle(O, 20, :fill)
end
```

```julia
@eps begin
    setline(10)
    sethue("purple")
    circle(O, 20, :fill)
end 1200 1200
```
