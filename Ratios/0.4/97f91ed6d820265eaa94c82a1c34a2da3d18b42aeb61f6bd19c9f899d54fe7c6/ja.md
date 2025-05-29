`Ratios`は、`Rational`の高速なバリアントである`SimpleRatio`を提供します。速度は、オーバーフローに対する脆弱性の増加と引き換えです。

APIの概要：

  * `r = SimpleRatio(num, den)`は`num // den`と同等です。
  * `common_denominator`は、`SimpleRatio`のコレクションを同じ分母に標準化し、それらの間のいくつかの算術演算がオーバーフローする可能性を低くします。
