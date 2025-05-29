```
CompositeBandRep{D} <: AbstractSymmetryVector{D}
```

`NewBandRep{D}`の線形有理係数の組み合わせを表す型です。

係数は一般に有理数である可能性がありますが、その重ね合わせは整数値のirrep重複度およびバンド占有数に対応しなければなりません。特に、そうでない場合、`SymmetryVector`への変換はエラーになります。

`brs`に含まれるインデックスからの構築については、[`CompositeBandRep_from_indices`](@ref)も参照してください。

## フィールド

  * `coefs::Vector{Rational{Int}}`: `brs`内の各バンド表現に関連付けられた係数ベクトル; `brs[i]`の係数は`coefs[i]`です。
  * `brs::Collection{NewBandRep{D}}`: `coefs`によって参照されるバンド表現。

## 例

### 脆弱な対称ベクトル

最初の例として、脆弱にトポロジカルな構成を表す`CompositeBandRep`を構築します（すなわち、負の整数係数を特徴とします）:

```julia
julia> brs = calc_bandreps(2);

julia> coefs = [0, 0, 1, 0, 0, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0, -1];

julia> cbr = CompositeBandRep(coefs, brs)
16-irrep CompositeBandRep{3}:
 (1g|Ag) + (1f|Aᵤ) + (1e|Ag) - (1a|Aᵤ) (2 bands)
```

関連する[`SymmetryVector`](@ref)を構築して、関連するirrepの内容を確認できます:

```julia
julia> SymmetryVector(cbr)
 [2Z₁⁺, 2Y₁⁻, 2U₁⁻, 2X₁⁺, 2T₁⁺, 2Γ₁⁺, 2V₁⁺, 2R₁⁺] (2 bands)
```

同様に、`cbr`が関連するバンド表現の単純な線形結合であることを確認できます:

```julia
julia> sum(c * brs[i] for (i, c) in enumerate(coefs)) == cbr
true
```

さらに、`cbr`で簡単な算術を行うこともできます（`CompositeBandRep`はモノイドの要素です）:

```julia
julia> cbr + 2cbr
3(1g|Ag) + 3(1f|Aᵤ) + 3(1e|Ag) - 3(1a|Aᵤ) (6 bands)
```

### 非自明な対称ベクトル

`CompositeBandRep`の係数は非整数であってもよく、全体の合計の関連するirrep重複度が整数である限り許可されます。したがって、`CompositeBandRep`はトポロジー的に非自明な対称ベクトル（および、拡張して任意の物理的対称ベクトル）を表すためにも使用できます:

```julia
julia> coefs = [-1//4, 0, -1//4, 0, -1//4, 0, 1//4, 0, 1//4, 0, 1//4, 0, -1//4, 0, 1//4, 1];

julia> cbr = CompositeBandRep{3}(coefs, brs)
16-irrep CompositeBandRep{3}:
 -(1/4)×(1h|Ag) - (1/4)×(1g|Ag) - (1/4)×(1f|Ag) + (1/4)×(1e|Ag) + (1/4)×(1d|Ag) + (1/4)×(1c|Ag) - (1/4)×(1b|Ag) + (1/4)×(1a|Ag) + (1a|Aᵤ) (1 band)

julia> SymmetryVector(cbr)
16-irrep SymmetryVector{3}:
 [Z₁⁺, Y₁⁻, U₁⁻, X₁⁻, T₁⁻, Γ₁⁻, V₁⁻, R₁⁻] (1 band)
```
