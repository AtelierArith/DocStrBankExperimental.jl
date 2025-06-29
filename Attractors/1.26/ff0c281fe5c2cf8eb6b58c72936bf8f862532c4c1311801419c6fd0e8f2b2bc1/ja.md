```
MatchBySSSetDistance(; distance = Centroid(), threshold = Inf, use_vanished = false)
```

IDを対応する状態空間セットの距離によって一致させるマッチャータイプです。

## キーワード引数

  * `distance = Centroid()`: [`setsofsets_distances`](@ref)に与えられる、一致させるための距離。
  * `threshold = Inf`: `threshold`より大きい距離を持つセットは互いにマッピングされないことが保証されます。
  * `use_vanished = !isinf(threshold)`: [`match_sequentially!`](@ref)で使用されるキーワード`use_vanished`の値。

## 説明

このマッチャーでは、比較される値は[`StateSpaceSet`](@ref)であり、ほとんどの場合、状態空間におけるアトラクタを表しますが、特徴のグループなど、他のセットを表すこともあります。

このマッチャーの動作は次のとおりです：（この会話では、セット/アトラクタが辞書に保存され、キー/IDがセットにマッピングされており、「新しい」辞書（`a₊`）のキーを「古い」辞書（`a₋`）のキーに一致させたいことを思い出してください）。

「古い」セットと「新しい」セットの間のすべての可能なセットペアの距離が、セット間の形式的な距離として計算されます。これは`distance`オプションによって制御され、`setsofsets_distances`(@ref)関数に与えられます。したがって、`distance`はその関数が受け入れるものであれば何でも構いません。つまり、[`Centroid`](@ref)、[`Hausdorff`](@ref)、[`StrictlyMinimumDistance`](@ref)のいずれか、または2つのセット`f(A, B)`を与えたときに正の数（その距離）を返す任意のユーザー提供関数`f`のいずれかです。

セット（特に、それに対応するID）は、この距離に従って一致させられます。まず、すべての可能なIDペア（古い、新しい）が、それに対応するセットの距離に従ってソートされます。最小距離のペアが一致します。一致したペアのIDは、一意のマッピングを確保するためにマッチングプールから削除されます。次に、残りの距離が最も少ないペアが一致し、このプロセスはすべてのペアが使い果たされるまで繰り返されます。

さらに、`threshold`値を提供することができます。2つのセット間の距離がこの`threshold`より大きい場合、2つのセットは置換マップで異なるIDが割り当てられることが保証され、そのため、`a₊`のセットは次に利用可能な整数をIDとして取得します。
