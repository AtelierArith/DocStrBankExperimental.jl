```
read_tle(str::AbstractString; verify_checksum::Bool = false) -> TLE
```

文字列 `str` に含まれる TLE を読み取ります。

!!! note
    `str` には **1つだけ**の TLE が含まれている必要があります。したがって、2行または3行の非空行が必要です。`#` で始まる行は無視されます。


# キーワード

  * `verify_checksum::Bool`: `true` の場合、両方の TLE 行のチェックサムが検証されます。そうでない場合、チェックサムは確認されません。(**デフォルト** = `true`)
