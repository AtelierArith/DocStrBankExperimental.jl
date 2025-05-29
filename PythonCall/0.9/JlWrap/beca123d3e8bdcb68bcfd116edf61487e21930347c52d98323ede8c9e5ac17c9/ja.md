```
pyfunc(f; [name], [qualname], [doc], [signature])
```

呼び出し可能な `f` を通常の Python 関数としてラップします。

名前、qualname、ドキュメンテーション文字列、またはシグネチャは、`name`、`qualname`、`doc`、または `signature` を使用してオプションで設定できます。

`Py(f)`（または `pyjl(f)`）とは異なり、`f` に渡される引数は常に `Py` 型であり、つまり決して変換されることはありません。
