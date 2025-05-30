```
struct Workspace{T1, T2, T3, T4, T5, T6}
```

# 引数:

  * `simple_input`: 入力オブジェクト `f` が呼び出される際に使用される、粒子を含まない
  * `simple_result`: 粒子なしの `f` からの単純な出力
  * `result`: 粒子を含む `f` の完全な出力
  * `buffersetter`: オブジェクト間でデータを移動させるためのヘルパー関数
  * `resultsetter`: オブジェクト間でデータを移動させるためのヘルパー関数
  * `f`: 呼び出す関数
  * `N`: 粒子の数
