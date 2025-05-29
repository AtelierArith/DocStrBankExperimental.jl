```
find_submodels(ode)
```

この関数は、ODEのシステムに基づいてすべての有効なサブモデルを計算し、返します。

入力:

  * `ode` - 研究対象のODEシステム

出力: 

  * `ode`オブジェクトとして表現されたサブモデルのリスト

例:

```
>ode = @ODEmodel(x1'(t) = x1(t)^2, 
                 x2'(t) = x1(t) * x2(t), 
                 y1(t) = x1(t), 
                 y2(t) = x2(t))
>find_submodels(ode)
    ODE{QQMPolyRingElem}[
        
        x1'(t) = a(t)*x2(t)^2 + x1(t)
        y1(t) = x1(t)
    ]
```
