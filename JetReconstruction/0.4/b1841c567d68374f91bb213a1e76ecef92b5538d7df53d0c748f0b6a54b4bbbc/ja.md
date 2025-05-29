```
ee_genkt_algorithm(particles::AbstractVector{T}; p = -1, R = 4.0,
                   algorithm::JetAlgorithm.Algorithm = JetAlgorithm.Durham,
                   recombine = +) where {T}
```

初期粒子のセットに対して e+e- 再構成アルゴリズムを実行します。

# 引数

  * `particles::AbstractVector{T}`: クラスタリングする粒子のベクトル。
  * `p = 1`: アルゴリズムのためのパワーパラメータ。Durham アルゴリズムが 1 に設定されている場合は必要ありません / 無視されます。
  * `R = 4.0`: ジェット半径パラメータ。Durham アルゴリズムの場合は必要ありません / 無視されます。
  * `algorithm::JetAlgorithm.Algorithm = JetAlgorithm.Durham`: 使用する特定のジェットアルゴリズム。
  * `recombine`: 使用する再結合スキーム。デフォルトは `+` です。

# 戻り値

  * ジェットクラスタリングの結果を `ClusterSequence` オブジェクトとして返します。

# 注意事項

これは e+e- ジェットクラスタリングアルゴリズムへの公開インターフェースです。この関数は、必要に応じてアルゴリズムとパワーパラメータの整合性をチェックします。その後、クラスタリング自体のために内部 EDM 粒子を準備し、実際の再構成メソッド `_ee_genkt_algorithm` を呼び出します。

アルゴリズムが Durham の場合、`p` は 1 に設定され、`R` は名目上 4 に設定されます。

`pp` 再構成とは異なり、アルゴリズムは明示的に指定する必要があることに注意してください。
