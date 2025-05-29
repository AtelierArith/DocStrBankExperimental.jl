```julia
ckbrief(
    file;
    dump,
    boundaries,
    relframes,
    idframes,
    tabular,
    single,
    bycoverage,
    utc,
    utcdoy,
    sclk,
    dpsclk,
    id,
    summarize,
    help,
    version,
    stdout,
    stderr,
    stdin,
    append,
    wait
)

```

CKBRIEFは、1つ以上のバイナリCKファイルの内容と時間カバレッジの概要を表示するコマンドラインユーティリティプログラムです。

# 拡張ヘルプ

!!! warning
    以下のすべての説明は、コマンドラインプログラムのヘルプ/使用出力から手動で解析されたものです。


| 引数           | 同等のもの     | 説明                         |
|:------------ |:--------- |:-------------------------- |
| `dump`       | `-dump`   | 補間間隔の境界を表示                 |
| `boundaries` | `-nm`     | セグメントの境界を表示                |
| `relframes`  | `-rel`    | 相対フレームを表示                  |
| `idframes`   | `-n`      | 構造IDに関連付けられたフレームを表示        |
| `tabular`    | `-t`      | 表形式で概要を表示                  |
| `single`     | `-a`      | すべてのファイルを単一のファイルとして扱う      |
| `bycoverage` | `-g`      | カバレッジでグループ化された概要を表示        |
| `utc`        | `-utc`    | UTCカレンダー日付形式で時間を表示         |
| `utcdoy`     | `-utcdoy` | UTC年の日形式で時間を表示             |
| `sclk`       | `-sclk`   | SCLK文字列として時間を表示            |
| `dpsclk`     | `-dpsclk` | SCLKティックとして時間を表示           |
| `id`         | `[ID]`    | [ID]を持つ構造の概要を表示            |
| `summarize`  | `-f`      | `[list]`ファイルにリストされたカーネルを要約 |
| `help`       | `-h`      | ヘルプを表示                     |
| `version`    | `-v`      | バージョンを表示                   |
