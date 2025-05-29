```
res = n4sid(data, r=:auto; verbose=false)
```

n4sidメソッドを使用して状態空間モデルを推定します。モデルは[`N4SIDStateSpace`](@ref)型のオブジェクトとして返され、`res.sys`としてアクセスされます。

「N4SID: Subspace Algorithms for the Identification of Combined Deterministic Stochastic Systems」PETER VAN OVERSCHEEおよびBART DE MOORからの簡略化されたアルゴリズム（アルゴリズム2）を実装しています。

周波数重み付けは「Frequency Weighted Subspace Based System Identification in the Frequency Domain」、Tomas McKelvey 1996からのアイデアを借用しています。特に、出力周波数重み行列（Fy）を、式（16）-（18）に現れるように適用します。

# 引数:

  * `data`: 同定データ `data = iddata(y,u)`
  * `r`: モデルのランク（モデル次数）
  * `verbose`: 情報を表示しますか？
  * `Wf`: 測定障害の周波数領域モデル。モデルを狭い周波数帯域に集中させるには、`Wf = Bandstop(lower, upper, fs=1/Ts)`のようなものを試して、この帯域の*外*に障害があることを示します。
  * `i`: アルゴリズムパラメータ、一般的に調整する必要はありません
  * `γ`: 不安定なモデルを安定化させるために(0,1)の間の値に設定し、最大固有値の大きさがγになるようにします。
  * `zeroD`: デフォルトはfalseです

異なる重み付け（n4sidがその一つ）を選択できる新しい実装[`subspaceid`](@ref)も参照してください。より正確な予測モデルは、閉ループデータに対してもバイアスがない[`newpem`](@ref)を使用することで得られることがあります。
