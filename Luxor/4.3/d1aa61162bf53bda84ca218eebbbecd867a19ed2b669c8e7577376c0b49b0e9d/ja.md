```
@png drawing-instructions [幅] [高さ] [ファイル名]
```

PNG描画を作成してプレビューします。オプションで幅と高さを指定できます（デフォルトは600x600です）。ファイルは、指定された場合は`ファイル名`として、指定されていない場合は`luxor-drawing(timestamp).png`として現在の作業ディレクトリに保存されます。

これらの「ショートカット」マクロは、便利さとタイピングの手間を省くために設計されています。マクロ`@png ⟦ body ⟧ 幅 高さ`は次のように展開されます：

```julia
Drawing(幅, 高さ, :png)
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
@png circle(O, 20, :fill)
```

```julia
@png circle(O, 20, :fill) 400
```

```julia
@png circle(O, 20, :fill) 400 1200
```

```julia
@png circle(O, 20, :fill) 400 1200 "/tmp/round"
```

```julia
@png circle(O, 20, :fill) 400 1200 "/tmp/round.png"
```

```julia
@png begin
    setline(10)
    sethue("purple")
    circle(O, 20, :fill)
end
```

```julia
@png begin
    setline(10)
    sethue("purple")
    circle(O, 20, :fill)
end 1200 1200
```
