```
subperiodicgroup(num::Integer, ::Val{D}=Val(3), ::Val{P}=Val(2))
subperiodicgroup(num::Integer, D::Integer, P::Integer)
                                                        --> ::SubperiodicGroup{D,P}
```

埋め込み次元 `D` と周期次元 `P` のサブ周期群 `num` の演算を `SubperiodicGroup{D,P}` として返します。

設定の選択肢は、国際結晶学表、ボリュームEのものです。

許可される `D` と `P` の組み合わせおよびそれに関連する群の名前は次のとおりです：

  * `D = 3`, `P = 2`: 層群 (`num` = 1, …, 80)。
  * `D = 3`, `P = 1`: 棒群 (`num` = 1, …, 75)。
  * `D = 2`, `P = 1`: フリゼ群 (`num` = 1, …, 7)。

## 例

```jldoctest
julia> subperiodicgroup(7, Val(2), Val(1))
SubperiodicGroup{2, 1} ⋕7 (𝓅2mg) with 4 operations:
 1
 2
 {m₁₀|½,0}
 {m₀₁|½,0}
```

## データソース

この関数によって返される対称操作は、元々 [ビルバオ結晶学データベース、SUBPERIODIC GENPOS](https://www.cryst.ehu.es/subperiodic/get_sub_gen.html) から取得されました。
