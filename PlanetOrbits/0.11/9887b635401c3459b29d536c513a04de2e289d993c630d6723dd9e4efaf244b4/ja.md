```
pmdec(orbit, t)
```

時刻 `t` [日] における *二次* の瞬時の適切運動異常 [mas/ジュリア年] を取得します。

```
pmdec(o)
```

`AbstractOrbitSolution` のインスタンスから *二次* の瞬時の適切運動異常 [mas/ジュリア年] を取得します。

```
pmdec(elem, t, M_planet)
```

時刻 `t` [日] における *一次* の瞬時の適切運動異常 [mas/ジュリア年] を取得します。`M_planet` と `elem.M` の単位は一致している必要があります。

```
pmdec(o, M_planet)
```

上記と同じですが、軌道解から取得します。
