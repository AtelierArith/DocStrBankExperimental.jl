```
normalize(df::DataFrame, normalizer::DataFrame; id = [:Analyte, :L], stats = (All(), "Accuracy"), colstats = :Stats)
```

与えられたノーマライザーによって `DataFrame` を正規化します。

# 引数

  * `normalizer`: `df` を正規化するための `DataFrame`。
  * `df`: 正規化される `DataFrame`。
  * `id`: 各行の一意のキーを持つ列（シンボル、文字列、または整数）。
  * `stats`: 正規化に関与する統計を表す `Tuple`。最初の引数は `df` に適用され、2番目の引数は `normalizer` に適用されます。`All()` はすべての統計を含むことを示します。
  * `colstats`: 統計の列名。
