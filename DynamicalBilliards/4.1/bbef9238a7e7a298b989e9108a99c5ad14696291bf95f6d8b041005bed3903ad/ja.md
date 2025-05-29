```
billiard_bunimovich(l=1.0, w=1.0)
```

Buminovichビリヤードを定義する`Obstacle`のベクトルを返します。これはスタジアムとも呼ばれます。長さは付属の半円を*含まない*と考えられ、ビリヤードの全長は`l + w`です。スタジアムの左端と右端は[`Semicircle`](@ref)です。

`billiard_stadium`は`billiard_bunimovich`のエイリアスです。
