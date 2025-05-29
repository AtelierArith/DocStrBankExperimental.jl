```
addmousestate!(scene, elements...)
```

`scene`とのすべてのマウスインタラクションによってトリガーされ、オプションで`elements`に指定されたすべてのプロットオブジェクトに制限される`Observable{MouseState}`を返します。

マウスイベントに反応するには、onmouse...ハンドラを使用します。

例:

```
mousestate = addmousestate!(scene, scatterplot)

onmouseleftclick(mousestate) do state
    # mousestateを使って何かをする
end
```
