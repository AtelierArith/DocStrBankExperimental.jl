```
data(z::AbstractProjectiveVector)
```

`z`の基になるベクトルにアクセスします。これは、射影構造を知らない関数にベクトルを渡すのに便利です。

```
data(z::AbstractVector)
```

一般的な`AbstractVector`の場合、これは単に恒等関数です。
