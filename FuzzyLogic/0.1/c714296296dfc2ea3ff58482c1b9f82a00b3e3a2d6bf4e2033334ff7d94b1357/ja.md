```
gensurf(fis::AbstractFuzzySystem; Npoints=100)
```

与えられたファジィ推論システムの生成サーフェスをプロットします。指定されたFISは、正確に1つの出力と最大2つの入力を持っている必要があります。

### 入力

  * `fis::AbstractFuzzySystem` – プロットするファジィ推論システム
  * `Npoints::Int64 (default 100)` – 生成サーフェスをプロットするために各入力に使用されるサンプルポイントの数。
