```julia
function membership(stat::RepMeasStatistic, ns::@NamedTuple{n::Int, k::Int})
```

適切な引数 `x` を作成して、[`_permTest!`](@ref) および [`_permMcTest!`](@ref) 関数で使用します。これは、`RepMeasStatistic` [グループ](@ref "Statistic groups") に属する検定統計量の置換スキームを使用して、[独自のテストを作成する](@ref "Create your own test") ときに使用します。

`stat` が `RepMeasStatistic` の場合、`ns` は名前付きタプルで、例えば `(n=N, k=K)` のようになります。ここで、$N$ は観測値の数（例：*被験者*）で、$K$ は測定値の数（または *処置*、*時間* など）です。詳細は [ns](@ref) を参照してください。

`collect(1:N*K)` を返します。

*例*

```julia
using PermutationsTests
membership(AnovaF_RM(), (n=2, k=4))
# ベクトル [1, 2, 3, 4, 5, 6, 7, 8] を返します
```
