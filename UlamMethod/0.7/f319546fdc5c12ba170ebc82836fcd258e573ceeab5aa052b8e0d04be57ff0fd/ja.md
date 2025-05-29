```
counts(data, ulam_result)
```

ベクトル `counts` を計算します。ここで `counts[i]` は i 番目のビン内のポイントの数に等しく、 `counts[end]` は境界の外にあるポイントの数（ニルヴァーナ内）です。

```
counts(traj, ulam_result)
```

`(counts(traj.x0, ulam_result), counts(traj.xT, ulam_result)` を計算します。
