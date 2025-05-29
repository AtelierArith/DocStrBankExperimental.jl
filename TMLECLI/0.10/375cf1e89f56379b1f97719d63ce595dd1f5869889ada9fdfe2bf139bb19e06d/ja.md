```
tmle(dataset; 
    estimands="factorialATE", 
    estimators="glmnet"; 
    verbosity=0, 
    outputs=Outputs(),
    chunksize=100,
    rng=123,
    cache_strategy="release-unusable",
    sort_estimands=false
)
```

TMLE CLI.

# 引数

  * `dataset`: データファイル（.csv または .arrow）

# オプション

  * `--estimands`: 文字列 ("factorialATE") またはシリアライズされた TMLE.Configuration（受け入れられるフォーマット: .json | .yaml | .jls）
  * `--estimators`: 使用する推定器を含むジュリアファイル。
  * `-v, --verbosity`: 冗長性レベル。
  * `-o, --outputs`: 生成される出力。
  * `--chunksize`: 結果は chunksize サイズのバッチで書き込まれます。
  * `-r, --rng`: ランダムシード（現時点では推定量の順序付けにのみ使用されます）。
  * `-c, --cache-strategy`: 嫌悪関数のキャッシング戦略、いずれかの ("release-unusable", "no-cache", "max-size")。

# フラグ

  * `-s, --sort_estimands`: キャッシュ使用量を最小限に抑えるために推定量をソートします（ブルートフォースアプローチが使用され、指数的に長いソート時間がかかります）。
