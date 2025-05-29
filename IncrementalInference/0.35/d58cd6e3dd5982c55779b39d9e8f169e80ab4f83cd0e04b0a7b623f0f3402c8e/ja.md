```julia
approxDeconv(fcto; ...)
approxDeconv(fcto, ccw; N, measurement, retries)

```

予測されたノイズ値の逆解を行い、(新しく計算された予測値と既知の測定値)のタプルを返します。

ノート

  * 現段階では、measurement::Tupleの最初の値にのみ対応しています。
  * "measured"は"calculated-predicted"値の解法の出発点として使用されます。
  * すべての因子評価ケースはまだサポートされていません。
  * 現在は`.threadid()==1`でのみ動作します。詳細は#1094を参照してください。
  * この関数はまだ初期実装の一部であり、一般化の改善が必要です。

開発ノート

  * TODO 複数の変数を持つさまざまなケースのテスト。
  * TODO マルチスレッドセーフにし、可能にする。詳細は#1094を参照してください。
  * TODO `nullhypo`を持つケースのテスト。
  * FIXME すべての使用ケースに対するFactorMetadataオブジェクト、空のオブジェクトだけではなく。
  * TODO #1096を解決する（マルチハイポ）。

      * TODO `multihypo`のテストケース。
  * TODO evalFactorとapproxConvを統合する方法があるかどうかを考える。

      * 基本的には、ユニークな値を持つサンプル1つのためのdeconvをどのように行うか（TAFに関して）。
  * TODO Nは100にハードコーディングされるべきではない。

関連

[`approxDeconv`](@ref), [`_solveCCWNumeric!`](@ref) ```
