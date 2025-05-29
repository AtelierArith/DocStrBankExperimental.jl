```
summary = read_summary(pth)
summary, raw_summary = read_summary(pth, extra_out = true)
```

`pth`からSUMMARYファイルを読み込みます。結果はDictとして提供されます。

# 注意事項

この関数は、`resdata` Pythonパッケージがインストールされている必要があります。これは、最初にPythonCallをインストールし、スクリプトまたはREPLに`using PythonCall`を記述すると、自動的に環境に追加されます。

主に`resdata.summary.Summary`を使用します。
