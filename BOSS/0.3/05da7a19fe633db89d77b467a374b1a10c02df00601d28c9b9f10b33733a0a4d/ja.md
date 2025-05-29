```
TuringBI(; kwargs...)
```

Turing.jlパッケージを使用してモデルパラメータとハイパーパラメータをサンプリングします。

# キーワード

  * `sampler::Any`: サンプルを引き出すために使用されるサンプリングアルゴリズム。
  * `warmup::Int`: 各チェーンでの初期未使用「ウォームアップ」サンプルの量。
  * `samples_in_chain::Int`: 各チェーンから使用されるサンプルの量。
  * `chain_count::Int`: サンプリングされた独立したチェーンの量。
  * `leap_size`: 各チェーンからは`leap_size`ごとにサンプルが使用されます。（相関のあるサンプルを避けるため。）
  * `parallel`: `parallel=true`の場合、チェーンは並行してサンプリングされます。

# サンプリングプロセス

各サンプリングされたチェーンでは;

  * 最初の`warmup`サンプルは破棄されます。
  * 次の`leap_size * samples_in_chain`サンプルからは、各`leap_size`ごとに1つが保持されます。

その後、すべてのチェーンからのサンプルが連結されて返されます。

引き出されたサンプルの合計:    'chain*count * (warmup + leap*size * samples*in*chain)' 返されたサンプルの合計: 'chain*count * samples*in_chain'
