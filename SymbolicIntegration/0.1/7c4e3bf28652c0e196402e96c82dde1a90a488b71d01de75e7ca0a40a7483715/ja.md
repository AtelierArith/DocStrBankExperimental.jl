```
TowerOfDifferentialFields(Hs) -> K, gs, D
```

微分体の塔を構築します。

与えられた `Hs = [H₁,...,Hₙ]` で `Hᵢ` は `C(x,t₁,...,tₙ)` にあり（すなわち、これらは変数 `x, t₁,...,tₙ` に関する多変数多項式の分数です）、`Hᵢ` は係数が `C(x, t₁,...,tᵢ₋₁` にある `tᵢ` の多項式として表現できる（特に、`Hᵢ` は `tᵢ₊₁,...,tₙ` に依存しない）場合、体 `K = C(x)(t₁)...(tₙ)` を返します。これは `C(x, t₁,...,tₙ)` と同型であり、`K` 上の導関数 `D` を返します。`K` は不確定元 `x`, `t₁`,...,`tₙ` を逐次的に付加することによって構成され、`C` は `D` の定数体であり、`D` は `C(x)` 上の `d/dx` であり、`D` は `C(x)(t₁)...(tᵢ₋₁)` から `C(x)(t₁)...(tᵢ)` へ逐次的に拡張され、`tᵢ` は `C(x)(t₁)...(tᵢ₋₁)` 上の単項式であり、`D(tᵢ)=Hᵢ=Hᵢ(x, t₁,....,tᵢ)` となります。生成元 `x` は `C` 上の `C(x)` のものであり、`tᵢ` は `C(x)(t₁)...(tᵢ)` の `C(x)(t₁)...(tᵢ₋₁)` 上のものであり、`gs=[x, t₁,...,tₙ]` として返されます。（注意：これらの生成元は、簡潔さのために同じ記号で示されていますが、同型であっても `C(x,t₁,...,tₙ)` の生成元 `x, t₁,...,tₙ` とは同一ではありません。）

# 例

```julia
R, (x, t1, t2) = PolynomialRing(QQ, [:x, :t1, :t2])
Z = zero(R)//1 # R の分数体の零要素
K, gs, D = TowerOfDifferentialFields([t1//x, (t2^2+1)*x*t1 + Z])
```

（注：多項式に `Z` を加えることによって、明示的にそれを分数体の要素に変換します。）
