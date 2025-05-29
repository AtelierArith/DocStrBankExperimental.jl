```
segments                = watershed(img, markers; compactness, mask)
```

画像をウォータシェッド変換を使用してセグメント化します。ウォータシェッド変換によって形成された各流域は、1つのセグメントに対応します。画像の局所最小値をマーカーとして使用している場合は、過剰セグメンテーションを避けるために[`hmin_transform`](@ref)の使用を検討してください。

パラメータ:

  * img            = 入力グレースケール画像
  * markers        = 各領域のマーカーに1から始まるインデックスが割り当てられた、imgと同じサイズの配列。ゼロはマーカーではないことを意味します。                     同じインデックスを持つ2つのマーカーは、それらの領域が1つの領域に統合されます。                     マーカーがブール配列の場合は、`label_components`を使用してください。
  * compactness    = 指定されたコンパクトネスパラメータを使用してコンパクトウォータシェッドアルゴリズムを使用します。大きな値は、より規則的な形状の                     ウォータシェッド流域をもたらします。[^1]
  * mask           = `mask`の値がtrueであるピクセルのみをセグメント化し、関心のある領域のみにセグメンテーションを制限するために使用されます

[^1]: https://www.tu-chemnitz.de/etit/proaut/publications/cws*pSLIC*ICPR.pdf

# 例

```jldoctest; setup = :(using ImageCore, ImageMorphology, ImageSegmentation)
julia> seeds = falses(100, 100); seeds[50, 25] = true; seeds[50, 75] = true;

julia> dists = distance_transform(feature_transform(seeds)); # シードからの距離を計算

julia> markers = label_components(seeds); # 各シードにユニークな整数IDを付与

julia> results = watershed(dists, markers);

julia> labels_map(results); # セグメント化された画像のラベル
```
