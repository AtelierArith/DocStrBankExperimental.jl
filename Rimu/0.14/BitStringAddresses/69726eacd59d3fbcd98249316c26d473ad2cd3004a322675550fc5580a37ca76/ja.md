```
new_address, value = hopnextneighbour(add, chosen, boundary_condition)
```

ハバードモデルのホッピングイベントの新しいアドレスを計算します。新しいアドレスと、関与するモードの占有数の積の平方根に境界条件に一致する項を掛けたものを `value` として返します。サポートされている境界条件は以下の通りです：

  * `:periodic`: 境界を越えるホッピングは `value` を変えません。
  * `:twisted`: 境界を越えるホッピングは `value` の符号を反転させます。
  * `:hard_wall`: 境界を越えるホッピングは `value` をゼロにします。
  * `θ <: Number`: 境界を越えるホッピングは、ホッピングの方向に応じて $\exp(iθ)$ または $\exp(−iθ)$ を掛けた `value` を返します。

オフダイアゴナルは以下のようにインデックス付けされています：

  * `(chosen + 1) ÷ 2` はホッピングサイトを選択します。
  * 偶数の `chosen` は左へのホップを示します。
  * 奇数の `chosen` は右へのホップを示します。

# 例

```jldoctest
julia> using Rimu.Hamiltonians: hopnextneighbour

julia> hopnextneighbour(BoseFS(1, 0, 1), 3)
(BoseFS{2,3}(2, 0, 0), 1.4142135623730951)

julia> hopnextneighbour(BoseFS(1, 0, 1), 4)
(BoseFS{2,3}(1, 1, 0), 1.0)

julia> hopnextneighbour(BoseFS(1, 0, 1), 3, :twisted)
(BoseFS{2,3}(2, 0, 0), -1.4142135623730951)

julia> hopnextneighbour(BoseFS(1, 0, 1), 3, :hard_wall)
(BoseFS{2,3}(2, 0, 0), 0.0)

julia> hopnextneighbour(BoseFS(1, 0, 1), 3, π/4)
(BoseFS{2,3}(2, 0, 0), 1.0000000000000002 + 1.0im)
```
