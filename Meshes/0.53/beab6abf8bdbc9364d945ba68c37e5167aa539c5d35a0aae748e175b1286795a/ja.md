```
∠(A, B, C)
```

レイBAとBCの間の角∠ABC。詳細は[https://en.wikipedia.org/wiki/Angle](https://en.wikipedia.org/wiki/Angle)を参照してください。

2Dでは範囲[-π, π]、3Dでは範囲[0, π]の値を返す`atan`の2引数形式を使用します。詳細は[https://en.wikipedia.org/wiki/Atan2](https://en.wikipedia.org/wiki/Atan2)を参照してください。

## 例

```julia
∠(Point(1,0), Point(0,0), Point(0,1)) == π/2
```
