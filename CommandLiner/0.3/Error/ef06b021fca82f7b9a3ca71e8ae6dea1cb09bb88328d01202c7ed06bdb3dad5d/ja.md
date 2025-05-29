```
erroruser(msg, exitcode=99)
EnduserError(msg, exitcode=99)
```

関数 `erroruser` は、`Base.error` と同様に `EnduserError` 例外をスローします。この例外は、*エンドユーザー* に明らかなエラーを通知するためのもので、例えば「ファイル 'foo' が見つかりません」や「無効なコマンドラインオプション '–foo'」などです。バックトレースは出力されません。この例外をキャッチした場合は、それを抑制するべきです。
