```
download!(granule::Granule, folder=".")
```

`granule`に関連付けられたファイルを`folder`にダウンロードします。ローカルに既に存在しない場合は、http(s)の場所からダウンロードされます。

[`netrc!`](@ref)を使用して設定できる資格情報（netrc）が必要です。
