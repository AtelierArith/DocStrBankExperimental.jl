このメソッドは、指定された生物物理モデルを使用してdMRIデータに対してマルチスレッドMCMC推定を実行し、ボクセルスレッディングメソッドを呼び出し、推定されたパラメータをniftiファイルとして保存します。 `savedir`には出力パスとファイル名のプレフィックスの両方が含まれます。 提供されたサンプラーが2つのサンプラーのタプルである場合、2段階MCMCサンプリングメソッドが実行され、最初のサンプラーを使用してすべての未知のパラメータをサンプリングし、次に最初のMCMCで残りのパラメータを事後平均に固定しながら、2番目のサンプラーでターゲット組織パラメータをサンプリングします。

```
threading(
    model_start::BiophysicalModel,
    sampler::Union{Sampler,Tuple{Sampler,Sampler}},
    dmri::MRI,
    mask::MRI,
    protocol::Protocol,
    noise_model::Noisemodel,
    savedir::String,
)
```

単一段階または二段階MCMCを使用して、サイズ[Nmeas, Nvoxels]の測定配列から推定値の平均と標準偏差を返すメソッド。

```
threading(
    model_start::BiophysicalModel,
    sampler::Sampler,
    measurements::Array{Float64,2},
    protocol::Protocol,
    noise_model::Noisemodel,
)


threading(
    model_start::BiophysicalModel,
    sampler::Tuple{Sampler,Sampler},
    measurements::Array{Float64,2},
    protocol::Protocol,
    noise_model::Noisemodel,
)
```
