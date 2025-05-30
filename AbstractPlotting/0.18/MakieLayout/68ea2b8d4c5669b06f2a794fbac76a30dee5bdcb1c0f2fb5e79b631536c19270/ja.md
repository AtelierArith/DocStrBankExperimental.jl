```
addmouseevents!(scene, elements...)
```

`scene`とのすべてのマウスインタラクションによってトリガーされ、オプションで`elements`に指定されたすべてのプロットオブジェクトに制限されるobservableを持つ`MouseEventHandle`を返します。

マウスイベントに反応するには、onmouse...ハンドラを使用します。

例:

```
mouseevents = addmouseevents!(scene, scatterplot)

onmouseleftclick(mouseevents) do event
    # mouseeventを使って何かをする
end
```
