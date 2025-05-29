```
spacegroup(sgnum::Integer, ::Val{D}=Val(3))
spacegroup(sgnum::Integer, D::Integer)          --> SpaceGroup{D}
```

与えられた空間群番号 `sgnum` と次元数 `D` に対する空間群対称操作を `SpaceGroup{D}` として返します。返される対称操作は、従来の基底ベクトルに対して指定されており、必ずしも原始的ではありません（[`centering`](@ref）を参照）。必要に応じて、原始単位胞の操作はその後、[`primitivize`](@ref) または [`Crystalline.reduce_ops`](@ref) を使用して生成できます。

従来の基底ベクトルのデフォルトの選択は、ビルバオ結晶学サーバー（または同等に、国際結晶学表）の規則に従っています。これらは次の通りです：

  * 単斜晶空間群のためのユニーク軸 *b*（セル選択1）。
  * Rhombohedral空間群のための表面三重六角単位胞。
  * 原点選択2：反転中心は (0,0,0) に配置されます。（二つの選択肢がある特定の中心対称空間群に関連しています；例えば、斜方晶、正方晶または立方晶系において）。

[`directbasis`](@ref) も参照してください。

## データソース

この関数によって返される対称操作は、元々 [ビルバオ結晶学サーバー、SPACEGROUP GENPOS](https://www.cryst.ehu.es/cryst/get_gen.html) から取得されました。関連する引用は次の通りです： ([Aroyo et al., Z. Kristallogr. Cryst. Mater. **221**, 15 (2006).](https://doi.org/10.1524/zkri.2006.221.1.15)).
