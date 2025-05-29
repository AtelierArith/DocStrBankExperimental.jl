```
@jog PkgName
```

`PkgName`のベンチマークを実行するための`JogPkgName`という名前のモジュールを作成します。

ベンチマークファイルへのほとんどの編集は、Revise.jlによって正しく追跡されます。もし追跡されない場合は、`@jog PkgName`を再実行して`JogPkgName`を完全に再読み込みしてください。

> 編集が自動的に追跡されるためには、`@jog PkgName`を呼び出す前にReviseを読み込む必要があります。


## メソッド

  * `suite`       `PkgName`のベンチマークの`BenchmarkGroup`を返します
  * `benchmark`   ウォームアップ、チューニング、スイートを実行します
  * `run`         `BenchmarkTools.run(suite(), args...; kwargs...)`にディスパッチします
  * `save_benchmarks`     一意のファイル名を使用して`PkgName`のベンチマークを保存します

## 隔離されたベンチマーク

各ベンチマークファイルは、それぞれ独自のモジュールにラップされており、1つのファイルで読み込まれたコードが別のファイルで見えることを防ぎます（明示的にインクルードされない限り）。

## 例

```julia
using AwesomePkg, PkgJogger
@jog AwesomePkg
results = JogAwesomePkg.benchmark()
file = JogAwesomePkg.save_benchmarks(results)
```
