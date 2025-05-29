```
nigglibasis(Rs; rtol=1e-5, max_iterations=200)
```

与えられた原始基底ベクトル `Rs` に対して、対応するニグリ還元単位胞の基底 `Rs′` と、`Rs′ = transform(Rs, P)` となる変換行列 `P` を返します（[`transform`](@ref)を参照）。

## 定義

ニグリ還元基底 $(\mathbf{a}, \mathbf{b}, \mathbf{c})$ は、任意の格子に対する基底の一意の選択を表します（より正確には、基底ベクトルの長さ $|\mathbf{a}|, |\mathbf{b}|, |\mathbf{c}|$ と、$\mathbf{a}, \mathbf{b}, \mathbf{c}$ の間の相互角の一意の選択）。この一意性は、格子の比較を容易にするため、ニグリ還元手続きを計算する主な動機の一つです。さらに、関連するニグリ還元基底ベクトル $(\mathbf{a}, \mathbf{b}, \mathbf{c})$ は、いくつかの条件を満たします [^3]:

1. **「主」条件:**

      * 基底ベクトルは長さが増加する順にソートされています: $|\mathbf{a}| ≤ |\mathbf{b}| ≤ |\mathbf{c}|$。
      * 基底ベクトル間の角度はすべて鋭角またはすべて鈍角です。
2. **「特別」条件:**

      * $$
        |\mathbf{a}| = |\mathbf{b}|
        $$

        または `\mathbf{b}\cdot\mathbf{c} = \tfrac{1}{2}|\mathbf{b}|^2` のような「特別」な場合に適用されるいくつかの特別な条件があります。詳細は文献 [^3] を参照してください。

同等に、ニグリ還元基底は以下の幾何学的条件を満たします（文献 [^3] のセクション 9.3.1）:

  * 基底ベクトルは長さが増加する順にソートされています。
  * 基底ベクトルの合計長さが最小限である、すなわち ``|\mathbf{a}| + |\mathbf{b}|

      * |\mathbf{c}|`` が最小です。すなわち、関連するニグリ胞はブリュガー胞です。
  * 関連するブリュガー胞は、他のすべてのブリュガー胞の中で最大の偏差を持ちます。すなわち、基底ベクトルの角度 $α, β, γ$ は $|90° - α| + |90° - β| + |90° - γ|$ を最大化します。

## キーワード引数

  * `rtol :: Real`: 浮動小数点比較のためにGrosse-Kunstleveアプローチで使用される相対許容誤差（デフォルト: `1e-5`）。
  * `max_iterations :: Int`: Krivy-Gruberステップをサイクルする最大反復回数（デフォルト: `200`）。

## 実装

実装は、元々Krivy & Gruber [^1] によって記述されたアルゴリズムに従い、Grosse-Kunstleveらによって提案された安定性の修正を加えています [^2]（これがなければ、文献 [^1] で提案されたアルゴリズムは浮動小数点ハードウェアでは単に機能しません）。

[^1] I. Krivy & B. Gruber. A unified algorithm for determinign the reduced (Niggli) cell,     [Acta Crystallogr. A **32**, 297 (1976)](https://doi.org/10.1107/S0567739476000636). [^2] R.W. Grosse-Kunstleve, N.K. Sauter, & P.D. Adams, Numerically stable algorithms for the     computation of reduced unit cells,     [Acta Crystallogr. A **60**, 1 (2004)](https://doi.org/10.1107/S010876730302186X) [^3] Sections 9.2 & 9.3, International Tables of Crystallography, Volume A, 5th ed. (2005).
