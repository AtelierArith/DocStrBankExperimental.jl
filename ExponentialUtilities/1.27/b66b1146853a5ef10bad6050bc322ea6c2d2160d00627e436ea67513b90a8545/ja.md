```
expv_timestep(ts,A,b[;adaptive,tol,kwargs...]) -> U
```

時間ステッピングを使用して行列指数関数-ベクトル積を評価します

$$
u = \exp(tA)b
$$

`ts` は `u` の時間スナップショットの配列で、`U[:,j] ≈ u(ts[j])` となります。`ts` は単一の値でも構いません。その場合、最終結果のみが返され、`U` はベクトルになります。

Niesen & Wright の時間ステッピングの公式が使用されます [^1]。時間ステップ `tau` が指定されていない場合、Niesen & Wright の (17) に従って選択されます。`adaptive==true` の場合、Niesen & Wright の時間ステップとクリロフ部分空間サイズの適応スキームが使用され、その相対許容誤差はキーワードパラメータ `tol` を使用して設定できます。適応スキームのデルタおよびガンマパラメータも調整可能です。

内部ステップを出力するには `verbose=true` を設定します（デバッグ用）。他のキーワード引数については、内部で使用される `arnoldi` と `phiv` を参照してください。

この関数は、n-by-1 行列 `B` の代わりにベクトル `b` を使用した、より直感的なインターフェースを持つ `phiv_timestep` の特別なケースであることに注意してください。

[^1]: Niesen, J., & Wright, W. (2009). A Krylov subspace algorithm for evaluating the φ-functions in exponential integrators. arXiv preprint arXiv:0907.4631.
