```
add_dmi(sim::AtomisticSim, Dfun::Function; name="dmi")
```

システムに空間DMIを追加します。DMIは次のように定義されます。

$$
\mathcal{H}_\mathrm{dmi} = \sum_{\langle i, j\rangle}  \mathbf{D}_{i j} \cdot\left(\mathbf{m}_{i} \times \mathbf{m}_{j}\right)
$$

ここで、$\mathbf{D}_{i j}$はDMベクトルです。この関数は、メッシュ上のスピンの位置を表すインデックス`(i, j, k)`を受け取り、**配列**を返す必要があります。この配列の長さは隣接点の数の半分である必要があります。

例えば、`CubicMesh`の場合、この関数は配列`[(D1, D2, D3), (D4, D5, D6), (D4, D5, D6)]`を返す必要があります。ここで：

  * `(D1, D2, D3)`は、サイト`(i, j, k)`とサイト`(i+1, j, k)`の間のDMベクトルを表します。
  * `(D4, D5, D6)`は、サイト`(i, j, k)`とサイト`(i, j+1, k)`の間のDMベクトルを表します。
  * `(D7, D8, D9)`は、サイト`(i, j, k)`とサイト`(i, j, k+1)`の間のDMベクトルを表します。

配列の長さは隣接点の数の半分に対応します。なぜなら、交換相互作用は正の方向（すなわち、インデックスが増加する方向の隣接サイトとの相互作用）でのみ考慮されるからです。

#### 例：

```julia
function spatial_bulk_DMI(i, j, k)
    Dx = i < 10 ? 0.1meV : 0.2meV
    Dy = 0.1meV
    Dz = 0.3meV
    return [(Dx, 0, 0), (0, Dy, 0), (0, 0, Dz)]  # 配列を返します
end

add_dmi(sim, spatial_bulk_DMI)
```
