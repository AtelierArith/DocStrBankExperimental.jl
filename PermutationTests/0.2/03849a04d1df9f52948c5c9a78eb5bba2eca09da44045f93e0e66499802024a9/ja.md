```julia
function trendTest!(<same args and kwargs as `correlationTest!`>)
```

実際には [`correlationTest`](@ref) と [`correlationTest!`](@ref) のエイリアスです。

$$
N
$$

要素を持つ二つのベクトル `x` と `y` がデータ入力として提供されます。 `x` は指定されたトレンドであり、`y` は観測データを保持します。次に、`x` と `y` の間でピアソンの積モーメント相関検定が実施されます。

`x` は線形、ポリノミアル、指数、対数、冪、三角関数など、任意のトレンドを保持できます。

*方向性検定、置換スキームおよび正確な検定のための置換回数:* [`correlationTest`](@ref) に従います。

多重比較バージョン: [`trendMcTest`](@ref) と [`trendMcTest!`](@ref)

両方のメソッドは [UniTest](@ref) 構造体を返します。

*例*

```julia
using PermutationTests
# 上向きの線形トレンドをテストします
N=10
x=Float64.(collect(Base.OneTo(N))) # [1, 2, ..., N]
y=[1., 2., 4., 3., 5., 6., 7., 8., 10., 9.]
# 上向きの線形トレンドを期待していると仮定すると、 
# したがって相関は正であると予想され、
# 検定の力を高めるために右方向の検定を使用できます。
t = trendTest(x, y; direction=Right()) 
```
