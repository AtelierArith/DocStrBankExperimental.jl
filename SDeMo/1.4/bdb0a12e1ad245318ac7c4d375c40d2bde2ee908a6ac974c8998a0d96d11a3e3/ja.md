```
PCATransform
```

PCA変換はモデルの特徴を投影し、問題の次元を減少させる方法としても機能します。このメソッドはトレーニングインスタンスのみを使用し、`absences=true`キーワードが使用されない限り、現在のケースのみを使用することに注意してください。これにより、データリークが発生しないことが保証されます（検証データやラスターデータは使用されません）。

これは`MultivariateTransform{PCA}`のエイリアスです。
