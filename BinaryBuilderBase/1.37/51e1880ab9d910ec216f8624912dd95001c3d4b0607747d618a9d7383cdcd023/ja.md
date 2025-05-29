```
DirectorySource(path::String; target::String = basename(path), follow_symlinks=false)
```

`path`からマウントするローカルディレクトリを指定します。

ディレクトリの内容は`${WORKSPACE}/srcdir`にマウントされるか、提供された場合はオプションのキーワード`target`が指すサブディレクトリにマウントされます。`follow_symlinks`が`true`の場合、シンボリックリンクはターゲットのコピーに置き換えられます。
