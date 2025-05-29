```
GroupMark([ Pairs[] ]; [ named arguments ])
```

グループマークを作成します。

グループマークは、他のマークを含むことができる高レベルのマークです。また、ルートVega仕様が含むことができるすべての定義（軸、凡例、タイトルなどの定義）を含むこともできます。

# 例

```julia
gm = GroupMark(
    signals=[sig1, sig2],
    axes = [ xscale(orient="bottom"), yscale(orient="left") ],
    legends=[ (fill = cscale, title="type", titleFontSize=15) ],
    marks= [ linemark, pointmark ],
)
```
