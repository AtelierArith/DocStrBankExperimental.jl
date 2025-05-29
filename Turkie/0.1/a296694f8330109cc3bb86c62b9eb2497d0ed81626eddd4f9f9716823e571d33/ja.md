```
TurkieCallback(args...; kwargs....)
```

## 引数

  * オプション 1 :    `model::DynamicPPL.Model, plots::Series/AbstractVector=[:histkde, Mean(Float32), Variance(Float32), AutoCov(20, Float32)]`

与えられたモデルの各変数について、`plots`からの各`plot`がプロットされます。多次元変数には自動的にインデックスが追加されます。

  * オプション 2 :   `vars::NamedTuple/Dict`

シンボルとプロットの系列の各ペアをプロットします。多次元変数の場合は、例えば`Symbol("m[1]")`のようにシンボルを渡す必要があります。いくつかの例についてはドキュメントを参照してください。

## キーワード引数

  * `window=1000` : トレースをプロットするためのウィンドウを使用します。
  * `refresh=false` : `sample`が再度呼び出されるたびにプロットを最初から再起動します（まだ作業中）。
