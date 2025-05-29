位相一致性テスト画像で、ステップからラインに補間します。

このテスト画像は、上から下にかけて特徴タイプがステップエッジからラインフィーチャーに変化します。勾配ベースのエッジ検出器は、画像の上部にあるステップ状の特徴を正しくマークするだけで、画像の下部にある2つの特徴を誤ってマークしますが、位相一致性は上から下にかけて単一の特徴を正しくマークします。一般的に、自然画像はステップからラインまでの特徴タイプの全連続体のほぼ均一な分布を含んでいます。

```
Usage:
    img = step2line(sze; nscales=50, ampexponent=-1, ncycles=1.5, phasecycles=0.25)

Arguments:
      sze::Integer - テスト画像の行数、デフォルトは512です。

Keyword Arguments:
  nscales::Integer - 信号を構成するために使用されるフーリエ成分の数。
                     デフォルトは50です。
 ampexponent::Real - 周波数に対する振幅の減衰指数。
                     -1の値は、振幅が周波数に反比例することを生成します
                     （ステップ特徴に対応します）。
                     -2の値は、ラインフィーチャーが三角波形として
                     現れることになります。デフォルトは-1です。
     ncycles::Real - 画像の幅にわたる波のサイクル数。
                     デフォルトは1.5です。
 phasecycles::Real - 画像の垂直方向に下がる特徴タイプの位相サイクル数。
                     デフォルトは0.25で、特徴の位相一致角が0からpi/2まで変化します。
Returns:
   img::Array{Float64,2} - テスト画像。


使用例:
  > img = step2line()                              # デフォルトパターン
  > img = step2line(ncycles=3, ampexponent=-1.5);  # 3サイクル、'ソフト' ステップからライン
  > img = step2line(ncycles=3, ampexponent=-1.5, phasecycles = 3);

```

参照:  [`circsine`](@ref), [`starsine`](@ref)
