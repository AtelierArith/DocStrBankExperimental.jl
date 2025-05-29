```
@process(process::String, doc::String=""; verbose::Bool=true)
```

このマクロは、プロセスのシミュレーションのための抽象型といくつかのボイラープレートコードを生成し、そのドキュメントを提供します。また、`verbose=true`の場合は、モデルを実装するための短いチュートリアルを出力します。

抽象プロセスタイプは、プロセスのすべてのモデル実装のスーパタイプとして使用され、「Abstract<ProcessName>Model」と名付けられます。*例*として、成長と呼ばれるプロセスの場合は`AbstractGrowthModel`となります。

`@process`への最初の引数は新しいプロセス名であり、2番目は`Abstract<ProcessName>Model`型に追加されるべき任意のドキュメントであり、3番目は短いチュートリアルを印刷するかどうかを決定します。

初心者はこのマクロを使用することを推奨されます。なぜなら、プロセスに対して次に何をすべきかを詳細に説明しているからです。しかし、より経験豊富なユーザーは、チュートリアルを印刷せずに直接プロセスを定義したいかもしれません。その場合は、新しい抽象型を定義し、それを`AbstractModel`のサブタイプとして定義するだけです。

```julia
abstract type MyNewProcess <: AbstractModel end
```

# 例

```julia
@process "dummy_process" "これは使用されるべきではないダミープロセスです"
```
