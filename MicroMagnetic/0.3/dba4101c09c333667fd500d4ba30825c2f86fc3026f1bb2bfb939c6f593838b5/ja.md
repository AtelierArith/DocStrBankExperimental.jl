```
add_exch(sim::AtomisticSim, Jfun::Function; name="exch")
```

システムに空間的な交換相互作用を追加するには、異なる空間点での交換パラメータを定義する関数を受け入れます。この関数は、メッシュ上のスピンの位置を表すインデックス `(i, j, k)` を受け取り、**配列**を返す必要があります。この配列の長さは隣接点の数の半分である必要があります。

例えば、`CubicMesh` の場合、関数は配列 `[Jx, Jy, Jz]` を返す必要があります。ここで：

  * `Jx` は、位置 `(i, j, k)` のサイトと位置 `(i+1, j, k)` のサイトとの間の交換相互作用を表します。
  * `Jy` は、位置 `(i, j, k)` のサイトと位置 `(i, j+1, k)` のサイトとの間の交換相互作用を表します。
  * `Jz` は、位置 `(i, j, k)` のサイトと位置 `(i, j, k+1)` のサイトとの間の交換相互作用を表します。

配列の長さは隣接点の数の半分に対応します。なぜなら、交換相互作用は正の方向（すなわち、インデックスが増加する方向の隣接サイトとの相互作用）でのみ考慮されるからです。

#### 例：

```julia
function spatial_J(i, j, k)
    Jx = i < 10 ? 1meV : 2meV
    Jy = 1meV
    Jz = 1meV
    return [Jx, Jy, Jz]  # 配列を返します
end

add_exch(sim, spatial_J)
```

この例では：

  * x方向の交換相互作用 (`Jx`) は、`i` の値に依存します。`i` が10未満の場合、`1meV` であり、それ以外の場合は `2meV` です。
  * y方向とz方向の相互作用 (`Jy` と `Jz`) は、`1meV` に固定されています。
