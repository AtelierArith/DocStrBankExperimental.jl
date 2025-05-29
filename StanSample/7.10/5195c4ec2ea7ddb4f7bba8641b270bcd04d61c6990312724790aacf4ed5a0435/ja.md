サマリー出力ファイルをstansummaryで作成したものを読み取ります。

```julia
read_summary(m)
read_summary(m, printsummary)

```

# 拡張ヘルプ

### 必要な引数

```julia
* `m`                                  : Stanモデルオブジェクト、例：SampleModel
```

### オプションの位置引数

```julia
* `printsummary=false`                 : cmdstanサマリーを印刷する
```

### 戻り値

```julia
* `df`                                 : cmdstanサマリーを含むデータフレーム
```
