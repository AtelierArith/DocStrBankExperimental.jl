```julia
chronos(
    file;
    from,
    fromtype,
    to,
    totype,
    format,
    time,
    sc,
    center,
    landingtime,
    sol1index,
    nolabel,
    trace,
    help,
    usage,
    template,
    stdout,
    stderr,
    stdin,
    append,
    wait
)

```

CHRONOSは、いくつかの時間システムと時間形式の間で変換するコマンドラインプログラムです。

# 拡張ヘルプ

!!! warning
    以下のすべての説明は、コマンドラインプログラムのヘルプ/使用出力から手動で解析されたものです。


| 引数            | 同等のもの                                    | 説明                  |
|:------------- |:---------------------------------------- |:------------------- |
| `from`        | `-FROM <"from" time system>`             | "from" 時間システム       |
| `fromtype`    | `-FROMTYPE <"from" time system type>`    | "from" 時間システムのタイプ   |
| `to`          | `-TO <"to" time system>`                 | "to" 時間システム         |
| `totype`      | `-TOTYPE <"to" time system type>`        | "to" 時間システムのタイプ     |
| `format`      | `-FORMAT <output time format picture>`   | 出力時間形式のピクチャ         |
| `time`        | `-TIME <input time>`                     | 入力時間                |
| `sc`          | `-SC <sc ID>`                            | sc ID               |
| `center`      | `-CENTER <cental body ID>`               | 中心天体のID             |
| `landingtime` | `-LANDINGTIME <UTC time of the landing>` | 着陸のUTC時間            |
| `sol1index`   | `-SOL1INDEX <index of the first SOL>`    | 最初のSOLのインデックス       |
| `nolabel`     | `-NOLABEL`                               |                     |
| `trace`       | `-TRACE`                                 |                     |
| `help`        | `-HELP`                                  | ヘルプを表示              |
| `usage`       | `-USAGE`                                 | 使用法を表示              |
| `template`    | `-TEMPLATE`                              | セットアップファイルテンプレートを表示 |
