```
test_reverse(f, Activity, args...; kwargs...)
```

`ReverseSplitWithPrimal`モードでの`f`の`Enzyme.autodiff_thunk`を有限差分に対してテストします。

`f`は、`Enzyme.autodiff_thunk`に渡される同じ引数のすべての制約を持ち、追加の制約があります：

  * 入力/出力に`Array{<:AbstractFloat}`が現れる場合、それの再形成されたバージョンも入力/出力に現れてはいけません。

# 引数

  * `Activity`: `f`の戻り値のアクティビティ。
  * `args`: 各エントリは、`f`への引数、`autodiff`によって受け入れられるアクティビティタイプ、または形式`(arg, Activity)`のタプルであり、ここで`Activity`は`arg`のアクティビティタイプです。指定されたアクティビティタイプがシャドウを必要とする場合、自動的に生成されます。

# キーワード

  * `rng::AbstractRNG`: ランダムな接線を生成するために使用する乱数生成器。
  * `fdm=FiniteDifferences.central_fdm(5, 1)`: 使用する有限差分法。
  * `fkwargs`: `f`に渡すキーワード引数。
  * `rtol`: `isapprox`の相対許容誤差。
  * `atol`: `isapprox`の絶対許容誤差。
  * `testset_name`: すべてのテストが評価されるテストセットに使用する名前。

# 例

ここではスカラーの関数のルールをテストします。`y`にアクティビティ注釈を提供しないため、`Const`であると見なされます。

```julia
using Enzyme, EnzymeTestUtils

x = randn()
y = randn()
for Tret in (Const, Active), Tx in (Const, Active)
    test_reverse(*, Tret, (x, Tx), y)
end
```

ここではバッチ逆モードの配列の関数のルールをテストします：

```julia
x = randn(3)
for Tret in (Const, Active), Tx in (Const, BatchDuplicated)
    test_reverse(prod, Tret, (x, Tx))
end
```
