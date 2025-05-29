```
vtcount([f=identity,] A::AbstractArray, dims=:)
```

`A`の要素のうち、`f`が真を返すものの数を、指定された`dims`にわたってカウントします。`f`が省略された場合、`A`の`true`要素の数をカウントします（これは`AbstractArray{Bool}`である必要があります）。スレッド対応。
