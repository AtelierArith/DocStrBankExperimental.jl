```
qplot2(x::Array{Float64}, y::Array{Float64}, time::Array{Float64}, name::String, style::String, lineWidth=1, symSize=1):: Int32
```

追加のパラメータ（時間？）情報を持つプロット。

## パラメータ:

```

'x', 'y': 線
'name' この線の名前
'style' 線のスタイル
'lineWidth' 線の幅
'symSize' シンボルのサイズ; 
'time' 各点の時間情報

```

## 例

```

julia-repl
julia> time=collect(0.0:0.01:10.0)
x = sin.(time)
y = cos.(time)
qfigure()
qplot(time, x + y, "function 1", "-b", 3)
qfigure()
qplot2(x, y, time, "function 2", "-m", 3)

```

両方のプロットにマーカーを使用し、両方のプロットで動くことを確認してください。

この関数は作成された線のIDを返します。うまくいけば、他の関数で使用できるでしょう。 IDはすべてが正常であれば >=0 であるべきで、エラーの場合は <0 です。
