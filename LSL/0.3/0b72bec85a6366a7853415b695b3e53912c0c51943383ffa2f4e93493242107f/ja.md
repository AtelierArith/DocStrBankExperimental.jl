```
StreamInfo
```

StreamInfo型はデータストリームの宣言を保存します。

次の情報を表します： a) ストリームデータ形式（#チャンネル、チャンネル形式） b) コア情報（ストリーム名、コンテンツタイプ、サンプリングレート） c) ストリームコンテンツに関するオプションのメタデータ（チャンネルラベル、測定単位など）

プログラムがラボネットワーク上で新しいストリームを提供したい場合、通常は最初にそのプロパティを説明するStreamInfoを作成し、その後にそれを使ってStreamOutletを構築し、ネットワーク上にストリームを作成します。アウトレットを発見した受信者はStreamInfoを照会できます。また、ストリームを録音する際にディスクに書き込まれ（ファイルヘッダーと同様の役割を果たします）。
