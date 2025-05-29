```
test_forward(f, Activity, args...; kwargs...)
```

`f`の`Enzyme.autodiff`を有限差分に対して`Forward`モードでテストします。

`f`は、`Enzyme.autodiff`に渡される同じ引数のすべての制約を持ち、追加の制約があります：

  * 引数の1つを変更する場合、それを返す必要があります。

# 引数

  * `Activity`: `f`の戻り値の活動
  * `args`: 各エントリは、`f`への引数、`autodiff`で受け入れられる活動タイプ、または形式`(arg, Activity)`のタプルであり、ここで`Activity`は`arg`の活動タイプです。指定された活動タイプが接線を必要とする場合、ランダムな接線が自動的に生成されます。

# キーワード

  * `rng::AbstractRNG`: ランダム接線を生成するために使用する乱数生成器。
  * `fdm=FiniteDifferences.central_fdm(5, 1)`: 使用する有限差分法。
  * `fkwargs`: `f`に渡すキーワード引数。
  * `rtol`: `isapprox`の相対許容誤差。
  * `atol`: `isapprox`の絶対許容誤差。
  * `testset_name`: すべてのテストが評価されるテストセットに使用する名前。

# 例

ここではスカラーの関数のルールをテストします。`y`に活動注釈を提供しないため、`Const`であると見なされます。

```julia
using Enzyme, EnzymeTestUtils

x, y = randn(2)
for Tret in (Const, Duplicated, DuplicatedNoNeed), Tx in (Const, Duplicated)
    test_forward(*, Tret, (x, Tx), y)
end
```

ここでは、バッチフォワードモードの配列の関数のルールをテストします：

```julia
x = randn(3)
y = randn()
for Tret in (Const, BatchDuplicated, BatchDuplicatedNoNeed),
    Tx in (Const, BatchDuplicated),
    Ty in (Const, BatchDuplicated)

    test_forward(*, Tret, (x, Tx), (y, Ty))
end
```
