```
second_moment(im::IntensityMap; center=true)
```

画像の二次モーメントテンソルを計算します。デフォルトでは、`center` 引数によって指定される二次 **累積量** または中心化された二次モーメントを実際に返します。
