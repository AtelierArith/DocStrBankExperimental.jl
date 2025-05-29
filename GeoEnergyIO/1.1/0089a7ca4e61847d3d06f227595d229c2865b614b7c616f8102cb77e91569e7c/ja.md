```
init = read_init(fn)
init, raw_init = read_init(fn, extra_out = true)
```

`fn`からinitファイルを読み込みます。これはベースパスである必要があります（すなわち、`.RSRT`拡張子なし）。結果はDictとして返されます。

# キーワード引数

  * `extra_out`: trueの場合、解析されたデータに加えて生のPythonオブジェクトも返します。デフォルトはfalseです。
  * `actnum=missing`: 出力をアクティブセルに絞るために使用できるACTNUM配列。

# 注意事項

この関数は、`resdata` Pythonパッケージがインストールされていることを要求します。これは、最初にPythonCallをインストールし、スクリプトまたはREPLに`using PythonCall`を記述すると、自動的に環境に追加されます。

Python側で参照する主なクラスは`ResdataFile`です。
