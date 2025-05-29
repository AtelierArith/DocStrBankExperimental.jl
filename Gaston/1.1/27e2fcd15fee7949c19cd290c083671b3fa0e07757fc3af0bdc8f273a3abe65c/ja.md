```
stem(x, y, onlyimpulses=false, [,axes] [, curve], args...) -> Gaston.Figure
```

`x` と `y` を使用してステムプロットを作成します。`onlyimpulses` が true の場合、各サンプルを示す従来の円は描画されません。

```
stem(x, f::Function, onlyimpulses=false, [,axes] [, curve], args...) -> Gaston.Figure
```

`y = f.(x)` を使用します。
