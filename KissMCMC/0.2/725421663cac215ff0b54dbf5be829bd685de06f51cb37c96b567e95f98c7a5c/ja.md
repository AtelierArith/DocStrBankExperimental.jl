```
emcee(pdf, theta0s;
      niter=10^5,
      nburnin=niter÷2,
      nthin=1,
      a_scale=2.0, # ステップスケールパラメータ。おそらく調整する必要はない
      use_progress_meter=true,
      hasblob=false,
      init_blobs=init_output_vector, # blobのストレージを初期化する、形式は (blob0, nsamples_walker) -> コンテナ
      reduce_blob!=(blobs, blob) -> push!(blobs, blob) # blobストレージに1つのblobを追加する
```

アフィン不変MCMCサンプラー、別名Pythonのemcee実装におけるMCハンマー

入力:

  * pdf – サンプリングする確率対数密度関数。

    ```
       pdfは任意のblobを返すこともできます。
       `p, blob = pdf(theta)` ここで `theta` はパラメータです。
    ```
  * theta0s – 初期パラメータ、ウォーカーの数の長さのベクトル。 `make_theta0s(theta0, ballradius)`を使って作成することを検討してください。

注意: theta0s[1]は `.+`、 `.*`、および `length` をサポートする必要があります。

オプションのキーワード入力:

  * niter – 取るステップの総数 (10^5) (==対数密度評価の総数)。
  * nburnin – 廃棄される初期ステップの総数、別名バーニング (niter/3)
  * nthin – n番目のサンプルのみを保存する (デフォルト=1)
  * use*progress*meter=true : 進捗メーターを表示するかどうか
  * hasblob=false – pdfがblobも返すかどうか
  * init*blobs=init*output_vector – 1つのウォーカーのblobのストレージを初期化する、形式は `(blob0, nsamples) -> コンテナ`
  * reduce_blob!=(blobs, blob) -> push!(blobs, blob) – 1つのblobをblobストレージに追加または削減する（1つのウォーカーの）

出力:

  * samples: 型とサイズ `Matrix{typeof(theta0)}(niter-nburnin, nwalkers)`
  * accept_ratio: 受け入れられたステップと総ステップの比率
  * logdensities: 各サンプルの対数密度の値
  * blobs: pdf関数が第二引数として返すその他のもの

ノート:

  * `squash_walkers(samples)`を使用して、すべてのウォーカーチェーンを1つに連結します。

参考文献:

  * Goodman, Jonathan, and Jonathan Weare, 2010 http://dx.doi.org/10.2140/camcos.2010.5.65
  * emcee https://github.com/dfm/emcee
  * Foreman-Mackey et al. 2013, emcee: The MCMC hammer, https://github.com/dfm/emcee

例

```
thetas, accept_ratio, logdensities = emcee(x->-sum(x.^2), [1.0, 2, 5, 8])
```
