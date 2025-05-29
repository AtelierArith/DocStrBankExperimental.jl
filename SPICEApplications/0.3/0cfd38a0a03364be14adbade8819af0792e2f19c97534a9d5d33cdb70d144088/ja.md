```julia
brief(
    file;
    tabular,
    single,
    centers,
    utc,
    utcdoy,
    etsec,
    sec,
    min,
    hour,
    day,
    bytime,
    bycoverage,
    byid,
    byname,
    body,
    center,
    at,
    from,
    to,
    listfile,
    help,
    version,
    stdout,
    stderr,
    stdin,
    append,
    wait
)

```

BRIEFは、1つ以上のバイナリSPKまたはバイナリPCKファイルの内容と時間カバレッジの概要を表示するコマンドラインユーティリティプログラムです。

# 拡張ヘルプ

!!! warning
    以下のすべての説明は、コマンドラインプログラムのヘルプ/使用出力から手動で解析されたものです。


| 引数           | 同等のもの         | 説明                             |
|:------------ |:------------- |:------------------------------ |
| `tabular`    | `-t`          | 概要を表形式で表示                      |
| `single`     | `-a`          | すべてのファイルを単一のファイルとして扱う          |
| `centers`    | `-c`          | 動きの中心/相対フレームを表示                |
| `utc`        | `-utc`        | UTCカレンダー日付形式で時間を表示（LSKが必要）     |
| `utcdoy`     | `-utcdoy`     | UTC年の日形式で時間を表示（LSKが必要）         |
| `etsec`      | `-etsec`      | J2000以降のET秒として時間を表示            |
| `sec`        | `-sec`        | 時間を「内側に丸めて」秒単位で表示              |
| `min`        | `-min`        | 時間を「内側に丸めて」分単位で表示              |
| `hour`       | `-hour`       | 時間を「内側に丸めて」時間単位で表示             |
| `day`        | `-day`        | 時間を「内側に丸めて」日単位で表示              |
| `bytime`     | `-s`          | 各ボディ/フレームの開始時間でソートされた概要を表示     |
| `bycoverage` | `-g`          | カバレッジでグループ化された概要を表示            |
| `byid`       | `-n`          | 数値IDコードを使用してボディ/フレームを表示        |
| `byname`     | `-o`          | ボディ/フレーム名で順序付けられた概要を表示         |
| `body`       | `-sb[bod]`    | ボディ[bod]の概要を表示                 |
| `center`     | `-sc[cen]`    | 動きの中心/相対フレーム[cen]の概要を表示        |
| `at`         | `-at [time]`  | カバレッジがエポック[time]を含む場合に概要を表示    |
| `from`       | `-from [beg]` | カバレッジが区間[beg]:[end]を含む場合に概要を表示 |
| `to`         | `-to [end]`   | カバレッジが区間[beg]:[end]を含む場合に概要を表示 |
| `listfile`   | `-f [list]`   | [list]ファイルにリストされたカーネルの概要を表示    |
| `help`       | `-h`          | ヘルプを表示                         |
| `version`    | `-v`          | バージョンを表示                       |
