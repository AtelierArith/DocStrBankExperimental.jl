```julia
sliding_window(
    xs,
    ys;
    min_segment_length,
    fit_threshold,
    fit_function,
    overlap
) -> Vector{Vector{Int64}}

```

`xs`を`min_segment_length`よりも長いセグメントに分割し、`fit_threshold`よりも良いフィットを持つものを選びます。デフォルトでは、フィットの良さは決定係数を使用して測定されます。各セグメントは`fit_threshold`の最小R²を持たなければなりません。ルート平均二乗誤差は、`fit_function = :rmse`を設定し、データセット依存の誤差閾値に`fit_threshold`を調整することで使用することもできます。この場合、ルート平均二乗誤差は`fit_threshold`よりも小さくなければなりません。

データをセグメント化するためにスライディングウィンドウアプローチを使用します：最初は空のセグメントが作成され、`fit_threshold`に達するまでデータが追加されます。次に新しいセグメントが作成され、このプロセスはデータが尽きるまで繰り返されます。デフォルトでは、セグメントの終わりは次のセグメントの始まりでもありますが、`overlap`を`false`に設定することで変更できます（結果として不連続なセグメンテーションになります）。

内部でデータを事前計算ステップとしてソートします。最も高速なセグメンテーションアルゴリズムが実装されていますが、最も正確ではありません。

インデックスの配列`[idxs1, ...]`を返します。ここで、`idxs1`は最初のセグメント内の`xs`のインデックスです。

# 例

```
segments = sliding_window(xs, ys; min_segment_length=1.2, fit_threshold=0.9)
```

関連情報: [`top_down`](@ref), [`shortest_path`](@ref).
