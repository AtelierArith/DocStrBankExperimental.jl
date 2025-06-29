```
icwt(res::AbstractArray, cWav::CWT, inverseStyle::InverseType=PenroseDelta())
```

逆ウェーブレット変換を3つの双対フレームのいずれかを使用して計算します。デフォルトでは、最小二乗法を使用して選択された重みを持つデルタ関数を使用します。以下の`PenroseDelta()`がデフォルトとして選ばれています。これは、モーレ波が標準的な双対フレーム（`dualFrames()`型）を使用すると壊滅的に失敗する傾向があるため、デフォルトとして選ばれています。

```
icwt(res::AbstractArray, cWav::CWT, inverseStyle::PenroseDelta)
```

単純な双対フレーム$β_jδ_{ji}$を使用して計算された逆連続ウェーブレット変換を返します。ここで、$β_j$は最小二乗問題$\|Ŵβ-1\|_2^2$を解くために選ばれ、$Ŵ$は`cWav`ウェーブレットのフーリエ領域表現です。この場合も`NaiveDelta()`の場合も、$δ$のフーリエ変換は定数関数であり、したがってこの最小二乗問題になります。

```
icwt(res::AbstractArray, cWav::CWT, inverseStyle::NaiveDelta)
```

単純な双対フレーム$β_jδ_{ji}$を使用して計算された逆連続ウェーブレット変換を返します。ここで、$β_j$はスケール因子$(^1/_s)^{^1/_p}$を打ち消すように選ばれます。一般的に、`PenroseDelta`を使用して重みを選択するよりも精度が低くなります。これはTorrenceとCompoで議論された方法です。

```
icwt(res::AbstractArray, cWav::CWT, inverseStyle::dualFrames)
```

標準的な双対フレーム$\tilde{\widehat{ψ}} = \frac{ψ̂_n(ω)}{∑_n\|ψ̂_n(ω)\|^2}$を使用して計算された逆連続ウェーブレット変換を返します。アルゴリズムは、標準的な双対フレームを使用して再度cwtを計算することです。その結果、3つのアルゴリズムの中で最も計算集約的であり、通常は最も良好に動作します。ただし、すべてのウェーブレットの高周波数が小さすぎる場合には数値的に不安定になり、この場合には壊滅的に失敗する傾向があります。
