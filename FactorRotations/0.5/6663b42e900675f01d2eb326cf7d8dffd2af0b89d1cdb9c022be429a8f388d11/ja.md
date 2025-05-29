```
ComponentLoss(loss::Function; orthogonal = false)
```

ユーザー定義の `loss` 関数を使用して、ロード行列の各要素に適用される [コンポーネント損失](@ref AbstractComponentLoss)因子回転メソッドの一般的な実装です。

## キーワード引数

  * `orthogonal`: `orthogonal = true` の場合は直交回転が行われ、それ以外の場合は斜交回転が行われます。（デフォルト: `false`）

## 例

### コンポーネント損失としてのクォータマックス

```jldoctest; filter = [r"(\d*)\.(\d{4})\d+" => s"\1.\2", r"var\"(.*)\"" => s""]
julia> L = [
           0.830 -0.396
           0.818 -0.469
           0.777 -0.470
           0.798 -0.401
           0.786  0.500
           0.672  0.458
           0.594  0.444
           0.647  0.333
       ];

julia> quartimax_loss = ComponentLoss(x -> x^4, orthogonal = true);

julia> L_component_loss = rotate(L, quartimax_loss)
FactorRotation{Float64} with loading matrix:
8×2 Matrix{Float64}:
 0.898755  0.194824
 0.933943  0.129749
 0.902131  0.103864
 0.876508  0.171284
 0.315572  0.876476
 0.251123  0.773489
 0.198007  0.714678
 0.307857  0.659334

julia> L_quartimax = rotate(L, Quartimax())
FactorRotation{Float64} with loading matrix:
8×2 Matrix{Float64}:
 0.898755  0.194823
 0.933943  0.129748
 0.902132  0.103864
 0.876508  0.171284
 0.315572  0.876476
 0.251124  0.773489
 0.198008  0.714678
 0.307858  0.659334

julia> isapprox(loadings(L_component_loss), loadings(L_quartimax), atol = 1e-5)
true
```
