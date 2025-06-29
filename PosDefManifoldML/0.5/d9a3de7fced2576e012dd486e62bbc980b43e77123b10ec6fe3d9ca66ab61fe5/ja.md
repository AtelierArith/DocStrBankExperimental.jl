```julia
mutable struct Compress <: Conditioner
    threaded
    β 
end
```

**圧縮**コンディショナーのための可変構造体。

正定値行列の多様体における点の集合$𝐏$が与えられたとき、次のように集合を変換します。

$$
βP_j, \ j=1,...,k
$$

、

ここで、$β$は変換された集合の平均ユークリッドノルムを最小化するように選ばれ、*すなわち*、指定されたメトリックに従って単位行列への平均距離です。

ユークリッドノルムは単位行列へのユークリッド距離であるため、再中心化された点の集合を圧縮することは、単位行列の周りの集合の平均分散を最小化します。したがって、コンディショナー[`Recenter`](@ref)の後に実行する必要があります。

この構造体には1つのフィールドのみがあります：

  * `.threaded`、計算がマルチスレッドで行われるかどうかを決定します（デフォルトはtrue）。

インスタンスを構築する際には、`threaded`のオプションキーワード引数のみを使用できます。

**適合したパラメータ**

コンディショナーが適合されると、次のフィールドが書き込まれます：

  * `.β`、適合した集合の平均ユークリッドノルムを最小化する正のスカラー。

**例**：

```julia
using PosDefManifoldML, PosDefManifold

# コンディショナーを作成
C = Compress()
```

**関連項目**：[`fit!`](@ref)、[`transform!`](@ref)、[`crval`](@ref)
