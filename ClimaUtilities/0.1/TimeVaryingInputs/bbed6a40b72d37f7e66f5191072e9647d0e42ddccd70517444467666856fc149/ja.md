```
TimeVaryingInput(func)
TimeVaryingInput(times, vals; method, context)
```

モデルの時間で与えられた関数/データを評価する方法を知っているオブジェクトを構築します。

# 関数を渡すとき

関数 `func` が渡されるとき、その関数はGPU互換でなければなりません（例：スプラインは不可）。

# 単一サイトデータを渡すとき

`times` と `vals` が渡されるとき、`times` はソートされている必要があり、2つの配列は同じ長さでなければなりません。

======= 入力が関数である場合、関数のシグネチャは `func(time, args...; kwargs...)` であることができます。関数は、`evaluate!` に渡された追加の引数とキーワード引数で呼び出されます。これを使用して、状態やキャッシュにアクセスし、それらを使用して出力フィールドを設定できます。

例えば：

```julia
CO2fromp(time, Y, p) = p.atmos.co2
input = TimeVaryingInput(CO2fromY)
evaluate!(dest, input, t, Y, p)
```
