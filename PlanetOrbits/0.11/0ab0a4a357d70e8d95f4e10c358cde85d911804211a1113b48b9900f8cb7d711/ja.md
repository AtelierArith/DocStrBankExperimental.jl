```
accdec(orbit, t)
```

*二次体*の右昇交点方向の瞬時加速度 [mas/ユリウス年^2] を時刻 `t` [日] に取得します。

```
accdec(o)
```

`AbstractOrbitSolution` のインスタンスから *二次体* の右昇交点方向の瞬時加速度 [mas/ユリウス年^2] を取得します。

```
accdec(elem, t, M_planet)
```

時刻 `t` [日] における *一次体* の右昇交点方向の瞬時加速度 [mas/ユリウス年^2] を取得します。`M_planet` と `elem.M` の単位は一致している必要があります。

```
accdec(o)
```

`AbstractOrbitSolution` のインスタンスから *一次体* の右昇交点方向の瞬時加速度 [mas/ユリウス年^2] を取得します。`M_planet` と `elem.M` の単位は一致している必要があります。
