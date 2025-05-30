```
download(granule::Granule, folder=".")
```

`granule`に関連付けられたファイルを`folder`にダウンロードします。ローカルに既に存在しない場合は、http(s)の場所からダウンロードします。新しいグラニュールを返します。変更を加えるバージョンについては、[`download!`](@ref)を参照してください。

[`netrc!`](@ref)を使用して設定できる資格情報（netrc）が必要です。
