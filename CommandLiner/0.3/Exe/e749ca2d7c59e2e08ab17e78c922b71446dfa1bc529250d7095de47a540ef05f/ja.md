```
exe([string, strin,..]; fail=true, onlystdout=stdout, splitlines=true)
```

コマンドを実行し、rc/stdout/stderrを取得するためのラッパーです。

`fail==true`の場合、非ゼロの終了コードで例外が発生します。

`onlystdout==true`の場合、`splitlines`に応じてstdoutから文字列または文字列のベクトルを返します。

`onlystdout==false`の場合、再び分割の有無に応じて(rc, out, err)-タプルまたは(rc, outs, errs)-タプルを返します。
