```
is_norm(K::AbsSimpleNumField, a) -> Bool, AbsSimpleNumFieldElem
```

整数または有理数である$a$に対して、$N(T) = a$が成り立つ$T \in K$を見つけるようにします。成功した場合はtrueと$T$を返し、そうでない場合はfalseといくつかの要素を返します。要素は因数分解された形で返されます。
