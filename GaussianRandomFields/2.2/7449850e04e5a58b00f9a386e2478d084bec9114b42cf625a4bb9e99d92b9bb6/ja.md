抽象型 `GaussianRandomFieldGenerator`

以下のガウス乱数場生成器が実装されています：

  * `Cholesky`: 共分散行列のコレスキー分解、正確ですが次元 `d` > 1 の乱数場には高コスト
  * `Spectral`: 共分散行列のスペクトル（固有値）分解、正確ですが次元 `d` > 1 の乱数場には高コスト
  * `KarhunenLoeve`: カルフネン・ローエフ展開、正確ではありませんが、低い切断次元で使用すると「滑らかな」乱数場に対して非常に効率的
  * `CirculantEmbedding`: 循環埋め込み法、正確で効率的ですが、構造化グリッド上の乱数場にのみ使用可能

参照：[`Cholesky`](@ref)、[`Spectral`](@ref)、[`KarhunenLoeve`](@ref)、[`CirculantEmbedding`](@ref)
