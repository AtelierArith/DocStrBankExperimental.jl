```
 getindex(surf, s, Inclusive())
```

`SurfaceSpace`の補足空間データ`s::Symbol`にアクセスします。オプションで、媒介壁の処理を通知するために`MedialWallIndexing`トレイト`Inclusive()`または`Exclusive()`を渡すことができます（デフォルトは`Inclusive()`です）。
