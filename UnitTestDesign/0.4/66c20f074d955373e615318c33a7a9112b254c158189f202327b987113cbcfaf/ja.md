```
all_tuples(parameters...; n_way, engine, disallow, seeds, wayness, Counter)
```

与えられたパラメータのタプルに基づいて、これらのパラメータのすべての `n_way` 組み合わせをカバーするテストケースを生成します。

# 引数

  * `engine=IPOG()`: `engine` は `IPOG()`, `GND()` または `Excursion()` です。
  * `disallow=nothing`: 禁止関数は、組み合わせが禁止されるべきときに `true` を返すパラメータの関数です。
  * `seeds=[]`: 生成されるテストケースの中に含める必要があるテストケースのリストです。
  * `wayness` は、`n_way` 組み合わせを増やすためのパラメータのサブセットを指定する辞書です。たとえば、組み合わせが二方向で、3番目から6番目のパラメータを三方向でカバーしたい場合は、`wayness = Dict(3 => [[3, 4, 5, 6]])` を使用します。
  * `Counter=Int` カウンターは計算に使用する整数型です。パラメータの整数数を保持できるだけ大きくなければなりません。

# 例

```julia
all_tuples([1, 2, 3], ["a", "b", "c"], [true, false]; n_way = 2)
parameters = fill(collect(1:3), 10)
all_tuples(parameters...; n_way = 4, engine = Excursion())
```
