```
metropolis(pdf, sample_ppdf, theta0;
           niter=10^5,
           nburnin=niter÷2,
           nthin=1,
           use_progress_meter=true,
           hasblob=false, # pdfがblobも返すかどうか
           init_blobs=init_output_vector, # blobのストレージを初期化する、形式は (blob0, nsamples) -> コンテナ
           reduce_blob!=(blobs, blob) -> push!(blobs, blob) # blobストレージに1つのblobを追加または削減する
```

メトロポリスサンプラー、最も単純なMCMCメソッド。対称提案分布（`ppdf`）でのみ使用可能です。

入力:

  * pdf – サンプリングする確率対数密度関数。

    ```
       それはまた、任意のblobを
       何かの第二出力引数として返すことができます。
       `p, blob = pdf(theta)` ここで `theta` はパラメータです。
    ```
  * sample*ppdf – 提案/ジャンプ分布のサンプルを引き出します                `sample*ppdf(theta)`。 対称である必要があります:`ppdf(theta1)==ppdf(theta2)`。 例:`theta -> c*randn() + theta`
  * theta0 – パラメータの初期値 (<:AbstractVector)

オプションのキーワード入力:

  * niter – 実行するステップ数 (10^5)
  * nburnin – 廃棄される初期ステップ数、別名バーニング (niter/3)
  * nthin – n番目のサンプルのみを保存する (デフォルト=1)
  * use*progress*meter=true : 進捗メーターを表示するかどうか
  * hasblob=false – pdfがblobも返すかどうか
  * init*blobs=init*output_vector – blobのストレージを初期化する、形式は (blob0, nsamples) -> コンテナ
  * reduce_blob!=(blobs, blob) -> push!(blobs, blob) – blobストレージに1つのblobを追加または削減する

注意:

  * シングルスレッド

出力:

  * サンプル:

      * if typeof(theta0)==Vector then Array{eltype(theta0)}(length(theta0), niter-nburnin)
      * if typeof(theta0)!=Vector then Array{typeof(theta0)}(niter-nburnin)
  * accept_ratio: 受け入れられたステップの比率
  * logdensities: 各サンプルの対数密度の値
  * blobs: pdf関数が第二引数として返すその他のもの
