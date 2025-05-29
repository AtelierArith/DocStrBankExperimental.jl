```
@svg 描画指示 [幅] [高さ] [ファイル名]
```

SVG描画を作成してプレビューします。オプションで幅と高さを指定できます（デフォルトは600x600です）。ファイルは、指定された場合は`filename`として現在の作業ディレクトリに保存され、指定されない場合は`luxor-drawing-(timestamp).svg`として保存されます。

### 例

```julia
@svg circle(O, 20, :fill)
```

```julia
@svg circle(O, 20, :fill) 400
```

```julia
@svg circle(O, 20, :fill) 400 1200
```

```julia
@svg circle(O, 20, :fill) 400 1200 "/tmp/test"
```

```julia
@svg circle(O, 20, :fill) 400 1200 "/tmp/test.svg"
```

```julia
@svg begin
    setline(10)
    sethue("purple")
    circle(O, 20, :fill)
end
```

```julia
@svg begin
    setline(10)
    sethue("purple")
    circle(O, 20, :fill)
end 1200 1200
```
