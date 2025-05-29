```
VolumePreservingAttention(dim, seq_length)
```

特定の次元とシーケンス長のために `VolumePreservingAttention` のインスタンスを作成します。

シーケンス長はデフォルトで `0` です。

すべてのシーケンス長に対して `seq_length` を `0` に設定しますが、高速 Cayley 活性化は適用されません。

# 引数

コンストラクタはオプションのキーワード引数で呼び出すことができます：

  * `skew_sym::Bool = false`：重み行列が歪対称であるか（`true`）または任意であるか（`false`）を指定します。

# ファンクタ

`VolumePreservingAttention` 型のレイヤーを適用すると、次のことが行われます：

  * まず、$Z \mapsto Z^T A Z =: C$ の操作を行います。ここで、$Z\in\mathbb{R}^{N\times\mathtt{seq\_length}}$ は時系列データを含むベクトルであり、$A$ はレイヤーに関連付けられた歪対称行列です（`skew_sym = true` の場合）。
  * 次のステップでは、$C$ の Cayley 変換を計算します； $\Lambda = \mathrm{Cayley}(C)$。
  * レイヤーの出力は $Z\Lambda$ となります。

# 実装

高速活性化はシーケンス長が 2、3、4、5 の場合のみ実装されています。他のシーケンス長は現在のところ CPU でのみ動作します。

高速 Cayley 活性化は、記号的に計算された逆数を使用しています。
