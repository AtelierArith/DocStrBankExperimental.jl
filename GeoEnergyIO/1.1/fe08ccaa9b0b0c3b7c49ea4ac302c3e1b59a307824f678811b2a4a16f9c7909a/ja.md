```
restart = read_restart(fn)
restart, raw_restart = read_restart(fn, extra_out = true)
```

`fn`から再起動ファイルを読み込みます。これは基本パスである必要があります（すなわち、`.RSRT`拡張子なし）。結果はDictのベクターとして提供されます。

# キーワード引数

  * `extra_out`: trueの場合、解析されたデータに加えて生のPythonオブジェクトも返します。デフォルトはfalseです。
  * `actnum=missing`: 出力をアクティブセルに減らすために使用できるACTNUM配列。
  * `egrid=missing`: 再起動を読み込むために必要なEGRIDオブジェクト。提供されない場合は、`fn`と同じパスから読み込まれます。

# 注意事項

この関数は、`resdata` Pythonパッケージがインストールされていることを要求します。これは、最初にPythonCallをインストールし、スクリプトまたはREPLに`using PythonCall`を追加すると、自動的に環境に追加されます。

Python側で検索する主なクラスは`ResdataRestartFile`です。
