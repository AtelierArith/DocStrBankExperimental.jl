# 最適化の型とコンストラクタ

最適化のトップレベルメソッドの設定。

### メソッド

```julia
Optimize(;
  method=Lbfgs(),
  iter=2000,
  save_iterations=false
)
```

### オプション引数

```julia
* `method::OptimizeMethod`      : 最適化アルゴリズム
* `iter::Int`                   : 総反復回数
* `save_iterations::Bool`       : 最適化の進行状況を出力にストリーム
```

### 関連ヘルプ

```julia
?Stanmodel                      : StanModelを作成する
?OptimizeAlgorithm              : 利用可能なアルゴリズム
```
