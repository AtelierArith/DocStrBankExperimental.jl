```
customembed(pts, positions::Positions, lags::Lags)
```

`customembed(pts, positions::Positions, lags::Lags)`を使用してカスタム状態空間再構成を行います。この関数はほぼ`DynamicalSystems.reconstruct`のように動作しますが、動的変数の順序に対してより柔軟性を持ち、負のラグを許可します。`positions`変数は、最終的な再構成でどの動的変数がどの変数にマッピングされるかを示し、`lags`は各埋め込み変数のラグを示します。

例: `customembed([rand(3) for i = 1:50], Positions(1, 2, 1, 3), Lags(0, 0, 1, -2)` は、状態ベクトル `(x1(t), x2(t), x1(t + 1), x3(t - 2))` を持つ4次元の埋め込みを生成します。

注意: `customembed`は*状態ベクトル*の配列を期待します。つまり、`pts[k]`はデータセットの`k`番目のポイントを参照し、`k`番目の動的変数/列を参照してはいけません。時系列のベクトルを埋め込むには、`DynamicalSystems`をロードし、最初に時系列を`Dataset`でラップします。例えば、`x = rand(100); y = rand(100)`が2つの時系列である場合、`customembed(Dataset(x, y), Positions(1, 2, 2), Lags(0, 0, 1)`は状態ベクトル `(x(t), y(t), y(t + 1))`を持つ埋め込みを作成します。

事前に埋め込まれたポイントは、位置/ラグの指示なしで単に`customembed(preembedded_pts)`を呼び出すことで`CustomReconstruction`インスタンスにラップできます。
