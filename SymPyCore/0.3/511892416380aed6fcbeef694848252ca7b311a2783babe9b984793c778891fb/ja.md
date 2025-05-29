```
Differential(x)
```

部分導関数を見つけるために使用します。

## 例

```
@syms x y u()
Dx = Differential(x)
Dx(u(x,y))  # diff(u(x,y),x) に解決されます
Dx(u)       # diff(u(x), x) を評価します
(Dx^2)(u(x))  # x における二回の導関数; 2u(x) の早期評価を避けるために () は付けません
```
