# 拡張ヘルプ

```
difference(X::Interval, Y::Interval)
```

### 出力

区間の位置に応じて、出力は次のいずれかになります。

  * `EmptySet`。
  * `Interval`。
  * 2つの`Interval`集合の`UnionSet`。

### アルゴリズム

$$
X = [a, b]
$$

および $Y = [c, d]$ を区間とします。これらの集合の差は $X ∖ Y = \{x: x ∈ X \text{ かつ } x ∉ Y \}$ であり、位置に応じて3つの異なる結果が得られます。

  * $$
    X
    $$

    と $Y$ が重ならない場合、すなわち交差が空である場合、集合の差は単に $X$ です。
  * そうでない場合、$Z = X ∩ Y ≠ ∅$ とし、$Z$ が $X$ を1つまたは2つの区間に分割します。後者のケースは、$Y$ の境界が $X$ に厳密に含まれるときに発生します。

厳密な包含を確認するために、包含が厳密であると仮定し、次に $Y$ との交差によって得られる $X$ をカバーする結果の区間（左側に1つ、右側に1つ、これを `L` と `R` とします）が平坦であるかどうかを確認します。3つのケースが考えられます。

  * `L` と `R` の両方が平坦であれば、$X = Y$ となり、結果は空集合です。
  * `L` のみが平坦であれば、結果は `R` であり、$Y$ によってカバーされていない残りの区間です。同様に、`R` のみが平坦であれば、結果は `L` です。
  * 最後に、どちらの区間も平坦でない場合、$Y$ は $X$ に厳密に含まれ、`L` と `R` の集合の和が返されます。

### 例

```jldoctest
julia> X = Interval(0, 2); Y = Interval(1, 4); Z = Interval(2, 3);

julia> difference(X, X)
∅(1)

julia> difference(X, Y)
Interval{Float64}([0, 1])

julia> difference(Y, Z)
UnionSet{Float64, Interval{Float64}, Interval{Float64}}(Interval{Float64}([1, 2]), Interval{Float64}([3, 4]))
```
