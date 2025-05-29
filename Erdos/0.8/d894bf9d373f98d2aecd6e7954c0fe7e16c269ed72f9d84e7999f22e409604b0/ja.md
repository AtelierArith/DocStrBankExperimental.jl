```
spring_layout(g; 
              k = 1 / √nv(g),
              maxiter = 100,
              inittemp = 2.0,
              [x0, y0]) -> x, y
```

グラフ `g` のノードの位置を Fruchterman と Reingold のスプリング/反発モデルに従って返します。2つのノード間の距離 `d` に対する力は次のように与えられます。

```
f_a(d) =  d / k # 引力
f_r(d) = -k^2 / d^2 # 反発力:
```

`maxiter` は位置の更新回数です。`inittemp` はイテレーションごとの移動量を制御します。

初期位置は引数 `x0` と `y0` を通じて渡すことができます。

位置は [-1, +1]^2 のボックスに収まるように再スケーリングされます。

この関数は [GraphLayout.jl](https://github.com/IainNZ/GraphLayout.jl) から適応されています。
