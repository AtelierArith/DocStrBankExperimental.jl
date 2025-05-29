```
∠(u, v)
```

ベクトル `u` と `v` の間の角度。

2Dでは範囲[-π, π]、3Dでは範囲[0, π]の値を返す二引数形式の `atan` を使用します。詳細は[https://en.wikipedia.org/wiki/Atan2](https://en.wikipedia.org/wiki/Atan2)を参照してください。

## 例

```julia
∠(Vec(1,0), Vec(0,1)) == π/2
```
