```
radon(ob::Object3d)::Function
```

ユーザーが3Dオブジェクトの投影ビューを作成するために、任意の投影座標でサンプリングできる`(u,v,ϕ,θ)`の関数を返します。

ここで使用される座標系は、`ϕ=0`がオブジェクト$f(x,y,z)$の$y$軸に沿った線積分に対応しています。したがって、`ϕ`が増加すると、線積分は反時計回りに回転します。
