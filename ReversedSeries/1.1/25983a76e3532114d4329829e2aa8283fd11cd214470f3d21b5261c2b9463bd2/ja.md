```julia
regular_bullish_divergence(
    rf::ReversedSeries.ReversedFrame;
    indicator,
    low,
    upper,
    lower,
    age_threshold,
    gap_threshold,
    peak_threshold
) -> Any

```

与えられたインジケーターの通常の強気ダイバージェンスがインデックス1付近で検出された場合はtrueを返します。ダイバージェンスを検出するためにボリンジャーバンドが使用されるため、ダイバージェンスをテストするインジケーターに加えて、`rf`にその存在が必要です。

# キーワード引数

|             引数 |       デフォルト |                     説明 |
| --------------:| -----------:| ----------------------:|
|      indicator |    `:rsi14` | テストされるインジケーターの`rf`内の名前 |
|            low |        `:l` |   OHLCVの高値に対する`rf`内の名前 |
|          upper | `:bb_upper` |   BBの上部バンドに対する`rf`内の名前 |
|          lower | `:bb_lower` |   BBの下部バンドに対する`rf`内の名前 |
|  age_threshold |         `1` |                      ? |
|  gap_threshold |    `(7,30)` |                      ? |
| peak_threshold |       `9.0` |                      ? |

# 例

```julia-repl
julia> regular_bearish_divergence(rf)
```
