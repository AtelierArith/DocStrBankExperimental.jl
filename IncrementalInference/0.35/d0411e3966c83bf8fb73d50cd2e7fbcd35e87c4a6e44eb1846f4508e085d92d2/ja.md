```julia
getCliqueStatus(cliqdata)

```

特定のクリークが解決または数値初期化の状態に関している`::Symbol`ステータスを返します：

  * :needdownmsg
  * UPSOLVED
  * DOWNSOLVED
  * INITIALIZED
  * MARGINALIZED
  * NULL

ノート：

  * `NULL`はクリークの最初の未初期化状態を表します。
