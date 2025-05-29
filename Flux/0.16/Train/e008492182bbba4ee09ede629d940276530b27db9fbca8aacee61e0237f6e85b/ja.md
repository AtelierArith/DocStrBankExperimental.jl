```
train!(loss, model, data, opt_state)
```

`loss` 関数とトレーニング `data` を使用して、特定の最適化ルールに従って `model` のパラメータを改善します。`data` を一度繰り返し、各 `d in data` に対して、`d` がタプルであれば `loss(model, d...)` を評価し、そうでなければ `loss(model, d)` を評価します。

`model` が `Enzyme.Duplicated` であり、`Enzyme.jl` がロードされている場合、勾配は Enzyme で計算され、それ以外の場合は Zygote で計算されます。

例えば、これらの定義を使って...

```
data = [(x1, y1), (x2, y2), (x3, y3)]

loss3(m, x, y) = norm(m(x) .- y)        # モデルは最初の引数

opt_state = Flux.setup(Adam(), model)   # 最適化モーメンタの明示的なセットアップ
```

...`Flux.train!(loss3, model, data, opt_state)` を呼び出すと、次のようなループが実行されます：

```
for d in data
    ∂L∂m = gradient(loss3, model, d...)[1]
    update!(opt_state, model, ∂L∂m)
end
```

より柔軟性が必要な場合は、このループを自分で書くこともできます。この理由から、`train!` はあまり拡張性が高くありません。上記のループに対して、いくつかの機能を追加するだけです：

  * 損失が無限大または `NaN` の場合、`DomainError` で停止します。
  * [`@withprogress`](https://github.com/JuliaLogging/ProgressLogging.jl) を使用して進捗バーを表示します。

!!! compat "New"
    このメソッドは Flux 0.13.9 で追加されました。Flux ≤ 0.13 で使用されていたものから大きな変更があります：

      * もはや `Flux.params` の結果ではなく、`model` 自体を受け取ります。（これは Zygote の「暗黙的」パラメータ処理から移行するためです。）
      * `loss` はデータのみを受け取る関数ではなく、最初の引数として `model` 自体も受け取る必要があります。
      * `opt_state` は [`Flux.setup`](@ref) の結果であるべきです。このステップなしで `Adam()` のような最適化器を使用すると、警告が表示されるはずです。
      * コールバック関数はサポートされていません。（ただし、上記の `for` ループ内に任意のコードを含めることができます。）

