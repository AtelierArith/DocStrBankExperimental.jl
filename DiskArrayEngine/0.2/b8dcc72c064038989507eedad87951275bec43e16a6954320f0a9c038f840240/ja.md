```
interpolate_diskarray(a, conv)
```

ディスク配列を1つ以上の次元に沿って補間するための関数です。補間は、`dim_index => (source_axis,dest_axis)` のペアからなるリスト `conv` によって指定されます。たとえば、次元 (x,y,t) の入力配列を新しい座標 (x2,y2,t2) に補間するには、次のようにします。

``julia #古い座標 a = [i+j+k for i in 1:4, j in 1:5, k in 1:6]  #ソース座標 x = 5.0:5.0:20.0  y = 2.0:3.0:14.0  #ターゲット座標 x2 = 5.0:0.5:20.0  y2 = 1.5:1.0:14.5  r = interpolate_diskarray(a,(1=>(x,x2),2=>(y,y2)))`
