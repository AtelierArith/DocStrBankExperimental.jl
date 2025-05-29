```
GitSource(url::String, hash::String; unpack_target::String = "")
```

リモートGitリポジトリを`url`からクローンするように指定します。`hash`はクローン後にチェックアウトする40文字のSHA1リビジョンです。

リポジトリは`${WORKSPACE}/srcdir`にクローンされるか、提供された場合はオプションのキーワード`unpack_target`が指すサブディレクトリにクローンされます。
