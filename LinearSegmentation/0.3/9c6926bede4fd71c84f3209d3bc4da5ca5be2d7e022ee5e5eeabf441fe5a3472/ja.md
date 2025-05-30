```julia
top_down(
    xs,
    ys;
    min_segment_length,
    fit_threshold,
    fit_function,
    overlap
) -> Vector{Vector{Int64}}

```

`xs`を`min_segment_length`よりも長いセグメントに分割し、`fit_threshold`よりも良いフィットを持つものにします。デフォルトでは、フィットの良さは決定係数を使用して測定されます。各セグメントは`fit_threshold`の最小R²を持たなければなりません。ルート平均二乗誤差は、`fit_function = :rmse`を設定し、データセット依存の誤差閾値に`fit_threshold`を調整することで使用することもできます。この場合、ルート平均二乗誤差は`fit_threshold`よりも小さくなければなりません。

データを`fit_function`に従って最適なフィットを持つ2つの部分に再帰的に分割し、`min_segment_length`からの最小セグメント長の制限と`fit_threshold`からのフィットの良さの制限を遵守します。内部でデータをソートして前処理ステップを行います。デフォルトでは、セグメントの終わりは次のセグメントの始まりでもありますが、`overlap`を`false`に設定することで変更できます（結果として不連続なセグメンテーションになります）。

インデックスの配列`[idxs1, ...]`を返します。ここで、`idxs1`は最初のセグメントの`xs`のインデックスです。

# 例

```
segments = top_down(xs, ys; min_segment_length=1.2)
```

参照: [`sliding_window`](@ref), [`shortest_path`](@ref).
