```
deepcopy(px)
```

`px`からすべてのパーセルの`deepcopy`を含む新しいパーセレーションを作成します。ただし、`deepcopy(p::Parcel)`と同様に、サーフェスは参照のままであり、実際にはコピーされません。なぜなら、それは大きなオブジェクトである可能性があるからです。
