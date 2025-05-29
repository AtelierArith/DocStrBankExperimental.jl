```
mweightcla(y::AbstractVector; prior::Union{Symbol, Vector} = :prop)
mweightcla(Q::DataType, y::Vector; prior::Union{Symbol, Vector} = :prop)
```

指定されたクラスのサブトータルウェイトに基づいて、カテゴリ変数の観測ウェイトを計算します。

  * `y` : カテゴリ変数 (n) (クラスメンバーシップ)。
  * `Q` : データ型 (例: `Float32`)。

キーワード引数:

  * `prior` : クラスメンバーシップの事前確率のタイプ。可能な値は: `:prop` (比例)、`：unif` (一様)、または各クラスの事前ウェイトを与えるベクトル (ベクトルの場合、`mlev(y)`と同じ順序でソートされている必要があります)。

1に合計されるベクトル `w` (n) を含む `Weight` 型のオブジェクトを返します (関数 `mweight` を参照)。

## 例

```julia
using Jchemo

y = vcat(rand(["a" ; "c"], 900), repeat(["b"], 100))
tab(y)
weights = mweightcla(y)
#weights = mweightcla(y; prior = :prop)
#weights = mweightcla(y; prior = [.1, .7, .2])
res = aggstat(weights.w, y; algo = sum)
[res.lev res.X]
```
