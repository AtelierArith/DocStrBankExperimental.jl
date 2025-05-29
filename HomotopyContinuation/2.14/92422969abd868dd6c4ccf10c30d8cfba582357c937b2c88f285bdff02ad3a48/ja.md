```
polyhedral(F::Union{System, AbstractSystem};
    only_non_zero = false,
    endgame_options = EndgameOptions(),
    tracker_options = TrackerOptions())
```

システム `F` を2ステップで解きます。まず、[^\HS95] で提案されたように、`F` のサポートから導出された一般的なシステムをポリヘドラルホモトピーを使用して解き、その後 `F` に向かって係数-パラメータホモトピーを実行します。これにより、パストラッカー（[`PolyhedralTracker`](@ref) または [`OverdeterminedTracker`](@ref)）と開始解を計算するためのイテレータが返されます。

`only_non_zero` が true の場合、アルゴリズムは `only_non_zero = false` と比較して、より少ないパスを追跡するスタートシステムを設定します。この場合、追跡するパスの数は `F` のニュートン多面体の混合体積に等しくなります。計算された解には、すべての非ゼロ座標を持つ解が含まれます。

`only_non_zero` が `false` の場合、`F` のすべての孤立解が計算されます。この場合、追跡するパスの数は $supp(F_i) ∪ \{0\}$ の凸包の混合体積に等しくなります。詳細は [^\LW96] を参照してください。

```
function polyhedral(
    support::AbstractVector{<:AbstractMatrix},
    coefficientss::AbstractVector{<:AbstractVector{<:Number}};
    kwargs...,
)
```

解決すべきシステム `F` のサポートと係数を直接提供することも可能です。

[^HS95]: Birkett Huber and Bernd Sturmfels. “A Polyhedral Method for Solving Sparse Polynomial Systems.” Mathematics of Computation, vol. 64, no. 212, 1995, pp. 1541–1555

[^LW96]: T.Y. Li and Xiaoshen Wang. "The BKK root count in C^n". Math. Comput. 65, 216 (October 1996), 1477–1484.

### 例

私たちは、合計6つの孤立解を持つシステム `f` を考えますが、すべての座標が非ゼロであるものは3つだけです。

```julia
@var x y
f = System([2y + 3 * y^2 - x * y^3, x + 4 * x^2 - 2 * x^3 * y])
tracker, starts = polyhedral(f; only_non_zero = false)
# length(starts) == 8
count(is_success, track.(tracker, starts)) # 6

tracker, starts = polyhedral(f; only_non_zero = true)
# length(starts) == 3
count(is_success, track.(tracker, starts)) # 3
```
