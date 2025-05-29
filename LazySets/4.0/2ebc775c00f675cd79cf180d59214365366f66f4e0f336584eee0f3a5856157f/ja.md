```
forget_sets!(cms::CachedMinkowskiSumArray)
```

キャッシュされたミンコフスキー和に、保存された集合を忘れるように指示します（サポートベクトルは忘れません）。サポートベクトルがキャッシュされた各方向で計算された集合のみが忘れられます。

### 入力

  * `cms` – キャッシュされたミンコフスキー和

### 出力

忘れられた集合の数。

### 注意事項

この関数は、将来的に新しい方向が問い合わせられないという前提の下でのみ使用するべきです。そうでない場合、サポートベクトルの結果は不正確になります。

この実装は楽観的で、最初にすべての集合を削除しようとします。しかし、すべてのキャッシュされた方向についてサポートベクトルが事前に計算されていることも確認します。これが成り立たない場合、実装は上記が成り立つ最大のインデックス $k$ を特定し、その $k$ 個の最も古い集合のみを削除します。以下の例を参照してください。

### 例

```jldoctest
julia> x1 = BallInf(ones(3), 3.); x2 = Ball1(ones(3), 5.);

julia> cms1 = CachedMinkowskiSumArray(2); cms2 = CachedMinkowskiSumArray(2);

julia> d = ones(3);

julia> a1 = array(cms1); a2 = array(cms2);

julia> push!(a1, x1); push!(a2, x1);

julia> σ(d, cms1); σ(d, cms2);

julia> push!(a1, x2); push!(a2, x2);

julia> σ(d, cms1);

julia> idx1 = forget_sets!(cms1) # 両方の集合に対してサポートベクトルが計算されました
2

julia> idx1 = forget_sets!(cms2) # 最初の集合に対してのみサポートベクトルが計算されました
1
```
