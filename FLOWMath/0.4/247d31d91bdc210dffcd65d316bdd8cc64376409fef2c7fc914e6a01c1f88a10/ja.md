```
sigmoid_blend(fx::Tuple, xt::Tuple, x, hardness=50)
```

`fx`内の関数の結果をシグモイド関数を使用して滑らかに遷移させ、`xt`内の位置で関数間の遷移を行います。`hardness`は関数間の遷移の鋭さを制御します。
