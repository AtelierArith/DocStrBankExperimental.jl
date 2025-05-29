```
TBLogger(logdir[, tb_increment]; 
        time=time(), 
        prefix="",
        purge_step=nothing, 
        step_increment=1, 
        min_level=Logging.Info)
```

`logdir`フォルダにTensorBoardLoggerを作成します。2番目の（オプションの）引数は、`logdir`がすでに存在する場合の動作を指定します：デフォルトの選択肢`tb_increment`は、`logdir`に増加する番号1,2...を追加します。他の選択肢は、以前のフォルダを上書きする`tb_overwrite`と、既存のログに追加する`tb_append`です。

オプションのキーワード引数`prefix`を渡すことで、ファイル名の先頭にパスを追加できます（注意：ログディレクトリではなく）。`create_eventfile()`を参照してください。

`purge_step::Int`が渡されると、`purge_step`より前のすべてのステップはtensorboardによって無視されます（クラッシュした計算を再起動する場合に便利です）。

`min_level`は、tensorboardに記録されるメッセージの最小レベルを指定します。
