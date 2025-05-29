```
overapproximate(cap::Intersection{N, <:HalfSpace, <:AbstractPolytope},
                dirs::AbstractDirections;
                [kwargs]...
               ) where {N}
```

半空間と多面体の交差点を、テンプレート方向のセットを用いて過大評価します。

### 入力

  * `cap`    – 半空間と多面体の交差
  * `dirs`   – テンプレート方向
  * `kwargs` – サポート関数アルゴリズムに渡される追加引数

### 出力

各半空間の法線方向が `dirs` の要素によって与えられる H-表現の多面体。
