```
SampleList
```

重み付きサンプルのリストとして表現された一般的な分布。

# 引数

  * `samples::S`
  * `weights::W`: オプションで、デフォルトでは `fill(1 / N, N)` に相当し、ここで `N` は `samples` コンテナの長さです。
