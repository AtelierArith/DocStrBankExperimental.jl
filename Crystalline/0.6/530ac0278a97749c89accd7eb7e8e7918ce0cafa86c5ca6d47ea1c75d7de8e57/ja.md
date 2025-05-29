```
pgirreps(iuclab::String, ::Val{D}=Val(3); mullikken::Bool=false) where D ∈ (1,2,3)
pgirreps(iuclab::String, D; mullikken::Bool=false)
```

IUCラベル`iuclab`の次元`D`の（結晶学的）点群の不変表現を`Vector{PGIrrep{D}}`として返します。

次元`D`の可能なIUCラベルについては`Crystalline.PG_IUC2NUM[D]`を参照してください。

## 表記法

不変表現のラベリングはCDMLの規則に従っており[^1]、これは時折、例えばBradleyとCracknellの*The Mathematical Theory of Symmetry in Solids*（1972）でのものとは異なる場合があります。

代わりにMulliken（「分光学者」）の不変表現ラベルを使用するには、キーワード引数`mulliken = true`を設定します（デフォルトは`false`）。[`mulliken`](@ref)も参照してください。

## データソース

データはビルバオ結晶学サーバーから取得されています[^2]。この機能を明示的に使用する場合は、元の参考文献を引用してください[^3]。

## 参考文献

[^1]: Cracknell, Davies, Miller, & Love, Kronecher Product Tables 1 (1979).

[^2]: ビルバオ結晶学データベースの[Representations PG program](https://www.cryst.ehu.es/cgi-bin/cryst/programs/representations_point.pl?tipogrupo=spg)。

[^3]: Elcoro et al., [J. of Appl. Cryst. **50**, 1457 (2017)](https://doi.org/10.1107/S1600576717011712)
