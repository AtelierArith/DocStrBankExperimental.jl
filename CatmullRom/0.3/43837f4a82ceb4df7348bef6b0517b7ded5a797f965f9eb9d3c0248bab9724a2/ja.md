```
catmullrom(points, pointsperarc; extend=true)
catmullrom(xs, ys, pointsperarc; extend=true)
catmullrom(xs, ys, zs, pointsperarc; extend=true)
```

与えられたabcissa順の点のパス（点またはxsおよびysとして）と、点のペア間にフィットさせる分割数（最初と最後を除くすべての隣接点）を使用して、各セグメントをカバーする中心的なCatmull-Romスプラインを取得します。

デフォルトでは、外挿された最初と最後の点が入力点のシーケンスに固定されるため、すべての入力点が結果のシーケンスに含まれます（CatmullRomフィッティングには最初と最後の点は含まれません）。これを行わないことを希望する場合は、`extend=false`で関数を呼び出してください。

その外挿に使用されるスケールファクターを指定したい場合は、`extendbounds(points, scale=scalefactor)`を使用し、その結果をこの関数に`extend=false`で渡してください。
