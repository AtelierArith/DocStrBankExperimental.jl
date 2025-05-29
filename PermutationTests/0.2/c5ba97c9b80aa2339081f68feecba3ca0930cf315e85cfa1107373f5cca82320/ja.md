```julia
function membership(stat::IndSampStatistic, ns::Vector{Int})
```

関数 [`_permTest!`](@ref) と [`_permMcTest!`](@ref) で使用する適切な引数 `x` を作成します。これは、`IndSampStatistic` [グループ](@ref "Statistic groups") に属する検定統計量の置換スキームを使用して、[独自のテストを作成する](@ref "Create your own test") ために使用されます。

`stat` が `IndSampStatistic` であり、`ns` がグループの数を示すベクトル、すなわち正の整数のベクトル `[N1,...,NK]` である場合、ここで $K$ はグループの数、$N_k$ は $k^{th}$ グループの観測数です（[ns](@ref) を参照）。  

グループメンバーシップベクトル `[repeat (1, N1);...; repeat(K, Nk)]` を返します。

もし `rev=reverse` がキーワード引数として渡された場合、代わりにグループメンバーシップベクトル `[repeat (K, N1);...; repeat(1, Nk)]` を返します。これは、`PearsonR()` [統計量](@ref) を使用して独立サンプルのt検定を実行するために使用されます。例えば [`studentTestIS`](@ref) を参照してください。

*例*

```julia
using PermutationsTests
membership(AnovaF_IS(), [3, 4])
# ベクトル [1, 1, 1, 2, 2, 2, 2] を返します
```
