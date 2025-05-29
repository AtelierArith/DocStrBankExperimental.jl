```
dominance(df::AbstractDataFrame, dep::Symbol, indeps::Vector; 
    covars = [], fitstat = :McFadden, link = nothing, family = nothing,
    multithreads = true, wts = nothing)
```

優位性分析を実行します。

## オプション:

```
- df - 入力データフレーム
- dep - 従属変数 (シンボルのみ)
- indeps - シンボルのベクターまたはシンボルのタプル。タプルは変数のセットを作成するために使用されます
- covars - すべてのモデルに含める共変量。これらの変数は優位性分析には使用されません
- fitstat - GLMモデルに使用されるR2のバリアント。現在、:McFadden (デフォルト) と :Nagelkerke が利用可能です
- link - GLMモデルのリンク関数。設定されていない場合、標準的なリンク関数が選択されます。
- family - GLMモデルに必要です。
- multithreads - マルチスレッドをオフにするには `false` に設定します
- wts - 加重回帰のための重みのベクター
```
