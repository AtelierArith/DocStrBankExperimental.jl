```
histogram(data::Vector;
          bincount=30,
          bins=range(minimum(data),stop=maximum(data),length=bincount),
          xlabel="",
          ylabel="",
          title="",
          pen=Pen(color=NamedColor("MidnightBlue"),opacity=0.3))
```

`data`のヒストグラムを作成します。
