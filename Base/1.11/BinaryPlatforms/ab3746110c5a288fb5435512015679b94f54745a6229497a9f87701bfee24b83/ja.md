```
parse_dl_name_version(path::String, platform::AbstractPlatform)
```

動的ライブラリへのパスが与えられた場合、ファイル名からどの情報を抽出できるかを解析します。例えば、"lib/libfoo.so.3.2"のようなものが与えられた場合、この関数は`"libfoo", v"3.2"`を返します。パス名が有効な動的ライブラリでない場合、このメソッドはエラーをスローします。ファイル名からsoversionを抽出できない場合、例えば"libbar.so"のような場合、このメソッドは`"libbar", nothing`を返します。
