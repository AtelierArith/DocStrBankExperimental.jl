```
Section(A::Float64, E::Float64, G::Float64, Ix::Float64, Iy::Float64, J::Float64, ρ::Float64 = 1.)
Section(mat::Material, A::Float64, Ix::Float64, Iy::Float64, J::Float64)
```

要素に割り当てられた断面。

# フィールド

  * `A` 面積 [距離²]
  * `E` 弾性係数 [力/距離²]
  * `Ix` 名目強い慣性モーメント [距離⁴]
  * `Iy` 名目弱い慣性モーメント [距離⁴]
  * `J` ねじり定数 [距離⁴]
  * `ρ=1` 密度 [質量/距離³]
