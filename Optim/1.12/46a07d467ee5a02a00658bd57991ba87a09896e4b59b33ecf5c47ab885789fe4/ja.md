# ゴールデンセクション

## コンストラクタ

```julia
    GoldenSection(;)
```

## 説明

`GoldenSection` メソッドは、区間 `[a, b]` 上の単変数関数を最小化しようとします。アルゴリズムは常に、最大の区間と最小の区間の比が黄金比であるように、三つの最小化候補 `(c, d, e)` のタプルを維持します。ここで、$c<d<e$ です。

## 参考文献

https://en.wikipedia.org/wiki/Golden-section_search
