```
TxIn
```

各非コインベース入力は、以前のトランザクションからのアウトポイントを消費します。`TxIn`は以下で構成されています。

  * `prevout::Outpoint`、消費される前のアウトポイント
  * `scriptsig::Vector{UInt8}`、アウトポイントのpubkeyスクリプトに置かれた条件を満たすもの。データプッシュのみを含むべきです。
  * `sequence::UInt32`番号。Bitcoin Coreおよびほとんどの他のプログラムのデフォルトは`0xffffffff`です。
