```julia
evaluate_GMM(X, GMM, k; ...)
evaluate_GMM(X, GMM, k, dic; compute_symKL, compare_EM)

```

データ `X` に対する `GMM` の対数尤度を計算し、生成モデルが `dic[:non_numerical][:dsGMM]` として渡された場合は対称KLダイバージェンスも計算します（TODO: これをもっとクリーンにする）。`compare_EM` が真であれば、`GaussianMixtures` パッケージのEMアルゴリズムを使用してデータ `X` にフィットしたGMMに対しても同じ量が計算されます。
