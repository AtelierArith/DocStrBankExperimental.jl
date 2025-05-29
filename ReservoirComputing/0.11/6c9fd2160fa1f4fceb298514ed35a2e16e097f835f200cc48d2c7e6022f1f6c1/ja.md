```
MRNN(activation_function, leaky_coefficient, scaling_factor)
MRNN(;activation_function=[tanh, sigmoid], leaky_coefficient=1.0,
    scaling_factor=fill(leaky_coefficient, length(activation_function)))
```

エコー状態ネットワーク（ESN）のための複数RNN（MRNN）初期化子を返します。これは、[^Lun2015]で紹介されました。

# 引数

  * `activation_function`: MRNNで使用される活性化関数のベクトル。
  * `leaky_coefficient`: MRNNで使用されるリーキー係数。
  * `scaling_factor`: 活性化関数を組み合わせるためのスケーリング係数のベクトル。

# キーワード引数

  * `activation_function`: MRNNで使用される活性化関数のベクトル。デフォルトは`[tanh, sigmoid]`です。
  * `leaky_coefficient`: MRNNで使用されるリーキー係数。デフォルトは1.0です。
  * `scaling_factor`: 活性化関数を組み合わせるためのスケーリング係数のベクトル。デフォルトは、すべての要素が`leaky_coefficient`に設定された`activation_function`と同じサイズの配列です。

この関数は、指定された活性化関数、リーキー係数、およびスケーリング係数を持つMRNNオブジェクトを作成し、ESNのリザーバドライバとして使用できます。

[^Lun2015]: Lun, Shu-Xian, et al. "*A novel model of leaky integrator echo state network for time-series prediction.*" Neurocomputing 159 (2015): 58-66.
