```
BlobTracker{T <: AbstractCorrespondence}
```

例 `bt = BlobTracker(sizes=3:5, σw=2.0, σe = 10.0)`

# オプションのキーワード引数:

  * `params::KalmanParams`: カルマンフィルタのパラメータ `σw,σe` を保持します
  * `amplitude_th = 0.0001`: blobs は考慮されるために少なくともこの重要度を持つ必要があります
  * `kill_counter_th::Int = 10`: 割り当てられた測定がないままこのステップ数が経過すると、blob は死にます
  * `sizes::AbstractVector`: blobs が検出されるサイズスケールを決定する数のベクトル。 [`Images.blob_LoG`](@ref) のドキュメントを参照してください。
  * `preprocessor = ((storage, img)->nothing`: `img` を処理し、その結果を `storage` に保存する関数
  * `correspondence::AbstractCorrespondence = HungarianCorrespondence(p=1.0, dist_th=2)`: blobs が測定にどのように割り当てられるかを決定します
  * `mask = nothing`: blobs を無視したい場所では false、追跡したい場所では true のオプションのブール画像。
