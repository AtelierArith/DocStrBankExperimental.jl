```julia
function trendMcTest!(<same args and kwargs as correlationMcTest!>)
```

実際には、[`correlationMcTest`](@ref)および[`correlationMcTest!`](@ref)のエイリアスです。

`x`は任意の指定されたトレンド（線形、多項式、指数、対数、三角関数など）であり、`Y`は観測データを保持します。次に、`x`と`Y`内のすべての$M$ベクトルとの間で多重比較ピアソン積モーメント相関テストが実施されます。

方向性テスト、置換スキーム、および正確なテストのための置換回数：*単変量バージョン* [`trendTest`](@ref)または[`trendTest!`](@ref)に従います。

両方のメソッドは、[MultcompTest](@ref)構造体を返します。

*例*

```julia
using PermutationTests
# 上向きの線形トレンドをテストします
N=10
M=100
x=Float64.(collect(Base.OneTo(N))) # [1, 2,..., N]
# 以下で作成されたMベクトルのうち、1つだけが有意な相関を持っています
Y=[[1., 2., 4., 3., 5., 6., 7., 8., 10., 9.], ([randn(N) for m=1:M-1]...)];
# 上向きの線形トレンドを期待しているため、相関は正であると予想されます。
# したがって、テストのパワーを高めるために右方向のテストを使用します。
t = trendMcTest(x, Y; direction=Right()) 
```
