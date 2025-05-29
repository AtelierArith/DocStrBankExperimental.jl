```
blendadjust(ablend, center::Point, xscale, yscale, rot=0)
```

既存のブレンドをスケーリング、平行移動、回転させて、ブレンドの定義の元の位置から形状の位置がどれほど離れていても、形状を適切に満たすようにします。

例えば、あなたのブレンド定義がこれだった場合（`1`に注意）

```julia
blendgoldmagenta = blend(
    Point(0, 0), 0,                   # 最初の円の中心と半径
    Point(0, 0), 1,                   # 2番目の円の中心と半径
    "gold",
    "magenta"
)
```

これを、`pos`を中心に100単位の形状で使用するには、次のように呼び出します：

```
blendadjust(blendgoldmagenta, Point(pos.x, pos.y), 100, 100)
```

その後、`setblend()`を使用します：

```
setblend(blendgoldmagenta)
```
