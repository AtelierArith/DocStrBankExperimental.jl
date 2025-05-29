```
abstract type Sector end
```

単純なオブジェクトの（同型類の）表現のための抽象型（単位的およびピボタルな）（前）融合カテゴリにおいて、例えば有限またはコンパクト群の不可約表現など。サブタイプ `I<:Sector` は `GradedSpace` のラベルの集合として機能します。

新しい `I<:Sector` は以下のメソッドを実装する必要があります：

  * `one(::Type{I})`: `I` の単位元
  * `conj(a::I)`: $a̅$, $a$ の共役または双対ラベル
  * `⊗(a::I, b::I)`: $a ⊗ b$ のユニークな融合出力を持つ iterable（すなわち、多重度の場合は繰り返さない）
  * `Nsymbol(a::I, b::I, c::I)`: `a ⊗ b` における `c` の出現回数、すなわち多重度
  * `FusionStyle(::Type{I})`: `UniqueFusion()`, `SimpleFusion()` または `GenericFusion()`
  * `BraidingStyle(::Type{I})`: `Bosonic()`, `Fermionic()`, `Anyonic()`, ...
  * `Fsymbol(a::I, b::I, c::I, d::I, e::I, f::I)`: F-記号：スカラー（`UniqueFusion`/`SimpleFusion` の場合）または行列（`GenericFusion` の場合）
  * `Rsymbol(a::I, b::I, c::I)`: R-記号：スカラー（`UniqueFusion`/`SimpleFusion` の場合）または行列（`GenericFusion` の場合）

オプションとして

  * `dim(a::I)`: セクター `a` の量子次元
  * `frobeniusschur(a::I)`: `a` のフロベニウス・シュール指標
  * `Bsymbol(a::I, b::I, c::I)`: B-記号：スカラー（`UniqueFusion`/`SimpleFusion` の場合）または行列（`GenericFusion` の場合）
  * `twist(a::I)` -> セクター `a` のツイスト

さらに、`iterate` と `Base.IteratorSize` は単一型 [`SectorValues{I}`](@ref) に対して機能するようにする必要があります。
