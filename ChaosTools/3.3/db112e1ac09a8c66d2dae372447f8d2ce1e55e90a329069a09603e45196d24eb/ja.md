```
lyapunov_from_data(R::StateSpaceSet, ks; kwargs...)
```

与えられたデータセット `R` は、動的システムの軌道を表すことが期待されており、`k` ステップの時間で進化した近傍の状態間の平均対数距離 `E(k)` を計算して返します（`k` は整数でなければなりません）。`E` 対 `k` の傾きは、最大リャプノフ指数を近似します。

通常、`R` は時系列の遅延座標埋め込みの結果です（DelayEmbeddings.jlを参照）。

## キーワード引数

  * `refstates = 1:(length(R) - ks[end])`: データセットのどの状態を「参照状態」として使用するかを示すインデックスのベクターで、アルゴリズムは `refstates` に含まれるすべての状態インデックスに適用されます。
  * `w::Int = 1`: [ザイラーウィンドウ](@ref)。
  * `ntype = NeighborNumber(1)`: 近傍のタイプ。[`NeighborNumber`](@ref) または [`WithinRange`](@ref) のいずれか。詳細については [Neighborhoods](@ref) を参照してください。
  * `distance = FirstElement()`: 近傍の状態の対数距離で使用される距離関数の種類を指定します。許可される距離の値は `FirstElement()` または `Euclidean()` で、詳細については以下を参照してください。近傍を見つけるためのメトリックは常にユークリッド距離です。

## 説明

データセットが近傍の状態の指数的発散を示す場合、次の式が成り立つはずです。

$$
E(k) \approx \lambda\cdot k \cdot \Delta t + E(0)
$$

これは $k$ 軸の *明確に定義された領域* に対して成り立ち、ここで $\lambda$ は近似された最大リャプノフ指数です。$\Delta t$ は元の時系列におけるサンプル間の時間です。十分に良い `ks` を選択した場合、線形スケーリング領域が飽和領域よりも大きいと仮定して、引数 `(ks .* Δt, E)` を使用して [`linear_region`](@ref) で傾き（= $\lambda$）をすぐに特定できます。

この関数で使用されるアルゴリズムは Parlitz[^Skokos2016] に由来し、Kantz[^Kantz1994] に基づいています。要するに、各参照状態に対して近傍が評価されます。次に、この近傍内の各点について、参照状態と近傍状態間の対数距離が「時間」インデックス `k` が増加するにつれて計算されます。すべての参照状態に対するすべての近傍状態の平均が返される結果です。

`distance` が `Euclidean()` の場合、完全な `D` 次元点のユークリッド距離を使用します（距離 $d_E$ は ref.[^Skokos2016] に記載）。ただし、`distance` が `FirstElement()` の場合、`R` の点の *最初の要素のみ* の絶対距離を計算します（距離 $d_F$ は ref.[^Skokos2016] に記載されており、`R` が遅延埋め込みから来る場合に便利です）。

[^Skokos2016]: Skokos, C. H. *et al.*, *Chaos Detection and Predictability* - Chapter 1 (section 1.3.2), Lecture Notes in Physics **915**, Springer (2016)

[^Kantz1994]: Kantz, H., Phys. Lett. A **185**, pp 77–87 (1994)

```
