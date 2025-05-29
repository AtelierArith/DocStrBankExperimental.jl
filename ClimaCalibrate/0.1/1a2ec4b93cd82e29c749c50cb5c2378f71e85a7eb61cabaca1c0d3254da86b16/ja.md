```
initialize(eki::EKP.EnsembleKalmanProcess, prior, output_dir)
initialize(ensemble_size, observations, noise, prior, output_dir)
```

キャリブレーションを初期化し、初期パラメータのアンサンブルを `output_dir` 内のフォルダーに保存します。

EKP 構造体が指定されていない場合は、EKP 構造体を構築して返します。
