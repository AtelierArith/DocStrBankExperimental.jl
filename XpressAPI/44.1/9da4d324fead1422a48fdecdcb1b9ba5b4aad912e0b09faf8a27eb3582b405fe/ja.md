```
XPRS_EXTRASETELEMS
```

行列に対して許可するセットの初期の追加要素の数。（整数）

行列にセットを追加する場合、最大の効率を得るために、行列が入力される前に `EXTRASETELEMS` コントロールを設定してセット要素のためのスペースを予約する必要があります。これが行われない場合、自動的にサイズ変更が行われますが、ユーザーが実際に必要とする以上のスペースが割り当てられる可能性があります。

デフォルト値: `0`

ドメイン: 0~+INF
