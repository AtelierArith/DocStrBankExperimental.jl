```julia
firbasis(τ, sfreq; ...)
firbasis(τ, sfreq, name; interpolate, scale_duration)

```

*τ* 時間ベクトルの周りにスパース FIR 基底を生成します。サンプリングレートは *sfreq* です。これは、イベント応答の形状に関して何の仮定もできない場合に便利です。丸められていないイベントが供給されると、それらはサンプル間で分割されます。例えば、イベントの遅延 = 1.2 は "0.8" と "0.2" のエントリを生成します。

高度な使用法: 2 番目の入力はサンプルの持続時間である可能性があります - 注意: `times(firbasis)` は常に持続時間 = 1 を仮定します。したがって、LMM と予測に関する問題が発生します！

# キーワード引数

`interpolate` (Bool, デフォルトは false): true の場合、サンプル間でイベントを線形に補間します。これにより、`predict` 関数は trailing 0 を返すようになります。``scale_duration`(Union{Bool,Interpolations-Interpolator}, デフォルトは false):     true の場合、応答をフィット引数の `eventfields` の 2 番目のエントリによってスケーリングします。つまり、FIR はインパルス応答ではなくステップ関数になります。     `Interpolations.interpolator` の場合、例えば `Interpolations.Linear()` - フィット引数の `eventfields` の 2 番目のエントリに基づいて FIR カーネルを伸ばすために `imresize` を使用します。これは Hassall を実装します。

# 例

-0.1s から 0.3s までの FIR 基底関数を 100Hz で生成します。

```julia-repl
julia>  f = firbasis([-0.1,0.3],100)
```

サンプル 103.3 で発生するイベントを評価します。

```julia-repl
julia>  f(103.3)
```
