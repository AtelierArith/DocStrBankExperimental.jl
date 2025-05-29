```
raysplit_indices(bd::Billiard, raysplitters::Tuple)
```

整数のベクトルを作成します。`i`番目のエントリは、ビリヤードの`i`番目の障害物に関連付けられている`raysplitters`タプルのエントリを示します。

`i`番目のエントリが`0`の場合、これは障害物がレイ分割を行わないことを意味します。
