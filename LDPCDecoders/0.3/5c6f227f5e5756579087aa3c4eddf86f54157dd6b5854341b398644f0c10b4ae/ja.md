与えられたパリティチェック行列、シンドローム、およびエラーをバッチデコードする関数

スクラッチスペースの割り当ては一度行われ、パフォーマンス向上のために再利用されます

# 引数

  * `decoder`: ビットフリップデコーダの設定
  * `syndromes`: バッチシンドロームを含むシンドローム行列
  * `errors`: この関数が操作する事前定義されたエラー行列

# 例

```jldoctest julia> decoder = BitFlipDecoder(LDPCDecoders.parity*check*matrix(1000, 10, 9), 0.01, 100);

julia> samples = 100

julia> errors = rand(1000,samples) .< 0.01;

julia> syndromes = zeros(900, samples);

julia> syndromes = H*errors .% 2

julia> guesses, successes = batchdecode!(decoder, syndromes, zero(errors));

julia> sum((guesses[:,i] == errors[:,i] for i in 1:samples)) > 0.995*samples
```
